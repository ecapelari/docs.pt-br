---
title: Segurança de acesso do código e o ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 93e099eb-daa1-4f1e-b031-c1e10a996f88
ms.openlocfilehash: ea5dbcc128f97ebbec72273378adb042bbe34e1e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759316"
---
# <a name="code-access-security-and-adonet"></a>Segurança de acesso do código e o ADO.NET
O .NET Framework oferece segurança baseada em função e segurança de acesso de código (CAS), ambas são implementadas por meio de uma infraestrutura comum fornecida pelo CLR (Common Language Runtime). No mundo do código não gerenciado, a maioria dos aplicativos é executada com as permissões do usuário ou da entidade de segurança. Como resultado, é possível que os sistemas de computador sejam danificados e os dados particulares sejam comprometidos quando um software mal-intencionado ou com erro for executado por um usuário com privilégios elevados.  
  
 Por sua vez, o código gerenciado em execução no .NET Framework inclui a segurança de acesso de código, que se aplica apenas ao código. O fato de o código ter a execução permitida ou não depende da origem do código ou de outros aspectos da identidade do código, não apenas da identidade da entidade de segurança. Isso reduz a probabilidade de que o código gerenciado seja mal-utilizado.  
  
## <a name="code-access-permissions"></a>Permissões de acesso de código  
 Quando o código é executado, ele apresenta evidências que são avaliadas pelo sistema de segurança CLR. Normalmente, essas evidências englobam a origem de código, incluindo a URL, o site e a zona, e as assinaturas digitais que garantem a identidade do assembly.  
  
 O CLR permite que o código realize apenas as operações que ele tem permissão para executar. O código pode solicitar permissões, e essas solicitações são respeitadas com base na política de segurança definida por um administrador.  
  
> [!NOTE]
>  O código executado no CLR não pode conceder permissões a ele mesmo. Por exemplo, o código pode solicitar e receber menos permissões do que uma política de segurança permite, mas nunca receberá mais permissões. Ao conceder as permissões, comece com nenhuma permissão e depois adicione as permissões mais restritas para a tarefa específica que está sendo executada. Começar com todas as permissões e depois negar permissões individuais resulta em aplicativos inseguros que podem conter brechas de segurança não intencionais para a concessão de mais permissões do que as necessárias. Para obter mais informações, consulte [NIB: configuração de política de segurança](http://msdn.microsoft.com/library/0f130bcd-1bba-4346-b231-0bcca7dab1a4) e [NIB: gerenciamento de política de segurança](http://msdn.microsoft.com/library/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9).  
  
 Existem três tipos de permissões de acesso de código:  
  
-   As `Code access permissions` são derivadas da classe <xref:System.Security.CodeAccessPermission>. São necessárias permissões para acessar recursos protegidos, como arquivos e variáveis de ambiente, e executar operações protegidas, como acessar código não gerenciado.  
  
-   As `Identity permissions` representam características que identificam um assembly. As permissões são concedidas a um assembly com base em evidências, o que pode incluir itens como uma assinatura digital ou a origem do código. As permissões de identidade também são derivadas da classe base <xref:System.Security.CodeAccessPermission>.  
  
-   As `Role-based security permissions` são baseadas no fato de uma entidade de segurança ter uma identidade especificada ou ser membro de uma função especificada. A classe <xref:System.Security.Permissions.PrincipalPermission> permite verificações de permissões declarativas e imperativas na entidade de segurança ativa.  
  
 Para determinar se o código está autorizado a acessar um recurso ou executar uma operação, o sistema de segurança do tempo de execução atravessa a pilha de chamadas, comparando as permissões concedidas de cada chamador com a permissão que está sendo exigida. Se algum chamador na pilha de chamadas não tiver a permissão exigida, uma <xref:System.Security.SecurityException> será gerada e o acesso será recusado.  
  
### <a name="requesting-permissions"></a>Solicitando permissões  
 A finalidade de solicitar permissões é informar ao tempo de execução quais permissões seu aplicativo requer para ser executado, e garantir que ele receberá apenas as permissões de que realmente precisa. Por exemplo, se seu aplicativo precisa gravar dados no disco local, ele requer a <xref:System.Security.Permissions.FileIOPermission>. Se essa permissão não for concedida, o aplicativo falhará quando tentar gravar no disco. Entretanto, se o aplicativo solicitar a `FileIOPermission` e essa permissão não for concedida, ele gerará a exceção no início e não será carregado.  
  
 Em um cenário onde o aplicativo precisa apenas ler dados do disco, você pode solicitar que ele nunca receba permissões de gravação. No caso de um bug ou um ataque mal-intencionado, seu código não pode danificar os dados em que opera. Para obter mais informações, consulte [NIB: solicitando permissões](http://msdn.microsoft.com/library/0447c49d-8cba-45e4-862c-ff0b59bebdc2).  
  
## <a name="role-based-security-and-cas"></a>Segurança baseada em função e CAS  
 Implementar a segurança baseada em função e a segurança de acesso de código (CAS) melhora a segurança geral de seu aplicativo. A segurança baseada em função pode ser baseada em uma conta do Windows ou uma identidade personalizada, tornando as informações sobre a entidade de segurança disponíveis ao thread atual. Além disso, os aplicativos são geralmente necessários para fornecer acesso a dados ou recursos com base nas credenciais fornecidas pelo usuário. Em geral, esses aplicativos verificam a função de um usuário e fornecem acesso aos recursos com base nas funções.  
  
 A segurança baseada em função permite que um componente identifique os usuários atuais e suas funções associadas em tempo de execução. Essas informações são então mapeadas por meio de uma política de CAS para determinar o conjunto de permissões concedidas em tempo de execução. Para um domínio de aplicativo especificado, o host pode alterar a política de segurança baseada em função padrão e definir uma entidade de segurança padrão que represente um usuário e as funções associadas a esse usuário.  
  
 O CLR usa permissões para implementar seu mecanismo de imposição de restrições em código gerenciado. As permissões de segurança baseada em função fornecem um mecanismo para descobrir se um usuário (ou o agente que atua em nome do usuário) tem uma identidade em particular ou é membro de uma função especificada. Para obter mais informações, consulte [permissões de segurança](http://msdn.microsoft.com/library/b03757b4-e926-4196-b738-3733ced2bda0).  
  
 Dependendo do tipo de aplicativo que você está criando, você também deve considerar implementar as permissões baseadas em função no banco de dados. Para obter mais informações sobre a segurança baseada em função no SQL Server, consulte [segurança do SQL Server](../../../../docs/framework/data/adonet/sql/sql-server-security.md).  
  
## <a name="assemblies"></a>Assemblies  
 Os assemblies formam a unidade fundamental de implantação, controle de versão, reutilização, escopo de ativação e permissões de segurança para um aplicativo .NET Framework. Um assembly fornece uma coleção de tipos e recursos que são criados para trabalhar em conjunto e formar uma unidade lógica de funcionalidade. Para o CLR, um tipo não existe fora do contexto de um assembly. Para obter mais informações sobre como criar e implantar assemblies, consulte [programação com Assemblies](../../../../docs/framework/app-domains/programming-with-assemblies.md).  
  
### <a name="strong-naming-assemblies"></a>Assemblies de nomes fortes  
 Um nome forte, ou assinatura digital, consiste na identidade do assembly, que inclui seu nome de texto simples, número de versão e informações de cultura (se fornecidas), além de uma chave pública e uma assinatura digital. A assinatura digital é gerada a partir de um arquivo de assembly usando a chave privada correspondente. O arquivo do assembly inclui o manifesto do assembly, o qual contém os nomes e os hashes de todos os arquivos que compõem o assembly.  
  
 Um assembly de nome forte oferece a um aplicativo ou componente uma identidade exclusiva que outro software pode usar para se referir a ele explicitamente. O nome forte impede que os assemblies sejam enganados por um assembly que contém código hostil. O nome forte também garante a consistência entre versões diferentes de um componente. Você deve dar nomes fortes aos assemblies que serão implantados no GAC (cache de assembly global). Para obter mais informações, consulte [Criando e usando assemblies de nomes fortes](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
## <a name="partial-trust-in-adonet-20"></a>Confiança parcial no ADO.NET 2.0  
 No ADO.NET 2.0, o Provedor de Dados .NET Framework para SQL Server, o Provedor de Dados .NET Framework para OLE DB, o Provedor de Dados .NET Framework para ODBC e o Provedor de Dados .NET Framework para Oracle podem agora ser todos executados em ambientes parcialmente confiáveis. Em versões anteriores do .NET Framework, somente <xref:System.Data.SqlClient> tinha suporte em aplicativos com confiança parcial.  
  
 Pelo menos um aplicativo parcialmente confiável que usa o provedor SQL Server deve ter permissões de execução e <xref:System.Data.SqlClient.SqlClientPermission>.  
  
### <a name="permission-attribute-properties-for-partial-trust"></a>Propriedades de atributo de permissão para confiança parcial  
 Para os cenários de confiança parcial, você pode usar membros <xref:System.Data.SqlClient.SqlClientPermissionAttribute> para restringir ainda mais os recursos disponíveis para o Provedor de Dados .NET Framework para SQL Server.  
  
 A tabela a seguir lista as propriedades <xref:System.Data.SqlClient.SqlClientPermissionAttribute> disponíveis e suas descrições:  
  
|Propriedade de atributo de permissão|Descrição|  
|-----------------------------------|-----------------|  
|`Action`|Obtém ou define uma ação de segurança. Herdada de <xref:System.Security.Permissions.SecurityAttribute>.|  
|`AllowBlankPassword`|Habilita ou desabilita o uso de uma senha em branco em uma cadeia de conexão. Os valores válidos são `true` (para habilitar o uso de senhas em branco) e `false` (para desabilitar o uso de senhas em branco). Herdada de <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`ConnectionString`|Identifica uma cadeia de conexão permitida. Várias cadeias de conexão podem ser identificadas. **Observação:** não têm uma ID de usuário ou senha em sua cadeia de conexão. Nesta versão, você não pode modificar restrições de cadeia de conexão usando a Ferramenta de Configuração do .NET Framework. <br /><br /> Herdada de <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictions`|Identifica os parâmetros de cadeia de conexão que são permitidos ou não. Parâmetros de cadeia de caracteres de Conexão são identificados no formulário  *\<nome de parâmetro > =*. Vários parâmetros podem ser especificados, sendo delimitados por um ponto e vírgula (;). **Observação:** se você não especificar `KeyRestrictions`, mas você definir `KeyRestrictionBehavior` propriedade `AllowOnly` ou `PreventUsage`, nenhum parâmetro de cadeia de caracteres de conexão adicionais é permitido. Herdada de <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictionBehavior`|Identifica os parâmetros de cadeia de conexão como os únicos parâmetros adicionais permitidos (`AllowOnly`), ou identifica os parâmetros adicionais que não são permitidos (`PreventUsage`). `AllowOnly` é o padrão. Herdada de <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`TypeID`|Obtém um identificador exclusivo para este atributo quando implementado em uma classe derivada. Herdada de <xref:System.Attribute>.|  
|`Unrestricted`|Indica se a permissão irrestrita ao recurso é declarada. Herdada de <xref:System.Security.Permissions.SecurityAttribute>.|  
  
#### <a name="connectionstring-syntax"></a>Sintaxe de ConnectionString  
 O exemplo a seguir demonstra como usar o elemento `connectionStrings` de um arquivo de configuração para permitir que somente uma cadeia de conexão específica seja usada. Consulte [cadeias de caracteres de Conexão](../../../../docs/framework/data/adonet/connection-strings.md) para obter mais informações sobre como armazenar e recuperar cadeias de caracteres de conexão de arquivos de configuração.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictions-syntax"></a>Sintaxe de KeyRestrictions  
 O exemplo a seguir habilita a mesma cadeia de conexão, permite o uso do `Encrypt` e `Packet``Size` opções de cadeia de caracteres de conexão, mas restringe o uso de outras opções de cadeia de caracteres de conexão.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Encrypt=;Packet Size=;"  
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-preventusage-syntax"></a>Sintaxe de KeyRestrictionBehavior com PreventUsage  
 O exemplo a seguir permite a mesma cadeia de conexão e todos os outros parâmetros de conexão, com exceção de `User Id`, `Password` e `Persist Security Info`.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="User Id=;Password=;Persist Security Info=;"  
    KeyRestrictionBehavior="PreventUsage" />  
</connectionStrings>  
```  
  
#### <a name="keyrestrictionbehavior-with-allowonly-syntax"></a>Sintaxe de KeyRestrictionBehavior com AllowOnly  
 O exemplo a seguir permite duas cadeias de conexão que também contêm os parâmetros `Initial Catalog`, `Connection Timeout`, `Encrypt` e `Packet Size`. Todos os outros parâmetros de cadeia de conexão são restritos.  
  
```xml  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Initial Catalog;Connection Timeout=;  
       Encrypt=;Packet Size=;"   
    KeyRestrictionBehavior="AllowOnly" />  
  
  <add name="DatabaseConnection2"   
    connectionString="Data Source=SqlServer2;Initial   
    Catalog=Northwind2;Integrated Security=true;"  
    KeyRestrictions="Initial Catalog;Connection Timeout=;  
       Encrypt=;Packet Size=;"   
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
### <a name="enabling-partial-trust-with-a-custom-permission-set"></a>Habilitando a confiança parcial com um conjunto de permissões personalizado  
 Para habilitar o uso de permissões <xref:System.Data.SqlClient> para uma zona específica, um administrador de sistema deve criar um conjunto de permissões personalizado e configurá-lo como o conjunto de permissões para uma zona específica. Os conjuntos de permissões padrão, como `LocalIntranet`, não podem ser modificados. Por exemplo, para incluir <xref:System.Data.SqlClient> permissões de código que tem um <xref:System.Security.Policy.Zone> de `LocalIntranet`, um administrador de sistema pode copiar o conjunto de permissões `LocalIntranet`, renomeie-o como "CustomLocalIntranet", adicione o <xref:System.Data.SqlClient> permissões, importar a permissão de CustomLocalIntranet definida usando o [Caspol.exe (ferramenta de política de segurança de acesso do código)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)e defina o conjunto de permissões `LocalIntranet_Zone` para CustomLocalIntranet.  
  
### <a name="sample-permission-set"></a>Conjunto de permissões de exemplo  
 A seguir está um conjunto de permissões de exemplo para o Provedor de Dados .NET Framework para SQL Server em um cenário parcialmente confiável. Para obter informações sobre como criar conjuntos de permissões personalizadas, consulte [NIB: Configurando permissões define usando Caspol.exe](http://msdn.microsoft.com/library/94e2625e-21ad-4038-af36-6d1f9df40a57).  
  
```xml  
<PermissionSet class="System.Security.NamedPermissionSet"  
  version="1"  
  Name="CustomLocalIntranet"  
  Description="Custom permission set given to applications on  
    the local intranet">  
  
<IPermission class="System.Data.SqlClient.SqlClientPermission, System.Data, Version=2.0.0000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
version="1"  
AllowBlankPassword="False">  
<add ConnectionString="Data Source=(local);Integrated Security=true;"  
 KeyRestrictions="Initial Catalog=;Connection Timeout=;  
   Encrypt=;Packet Size=;"   
 KeyRestrictionBehavior="AllowOnly" />  
 </IPermission>  
</PermissionSet>  
```  
  
## <a name="verifying-adonet-code-access-using-security-permissions"></a>Verificando o acesso de código ADO.NET usando permissões de segurança  
 Para cenários de confiança parcial, você pode exigir privilégios CAS para determinados métodos em seu código especificando um <xref:System.Data.SqlClient.SqlClientPermissionAttribute>. Se o privilégio não for permitido pela política de segurança restrita em vigor, uma exceção será gerada antes que seu código seja executado. Para obter mais informações sobre a política de segurança, consulte [NIB: gerenciamento de política de segurança](http://msdn.microsoft.com/library/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9) e [NIB: práticas recomendadas de política de segurança](http://msdn.microsoft.com/library/d49bc4d5-efb7-4caa-a2fe-e4d3cec63c05).  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como escrever um código que requer um cadeia de conexão específica. Ele simula a negação de permissões irrestritas a <xref:System.Data.SqlClient>, que um administrador de sistema implementaria usando uma política CAS no mundo real.  
  
> [!IMPORTANT]
>  Ao criar permissões CAS para ADO.NET, o padrão correto é começar com o caso mais restritivo (nenhuma permissão) e depois adicionar as permissões específicas que são necessárias para a tarefa em particular que o código precisa executar. O padrão oposto, começando com todas as permissões e, em seguida, negar uma permissão específica, não é seguro porque há várias maneiras de expressar a mesma cadeia de conexão. Por exemplo, se você iniciar com todas as permissões e depois tentar negar o uso da cadeia de conexão “server=someserver”, a cadeia de caracteres “server=someserver.mycompany.com” ainda será permitida. Ao iniciar sempre sem conceder absolutamente nenhuma permissão, você reduz as chances de haver brechas no conjunto de permissões.  
  
 O código a seguir demonstra como `SqlClient` realiza a exigência de segurança, que gera uma <xref:System.Security.SecurityException> caso as permissões CAS apropriadas não estejam estabelecidas. A saída <xref:System.Security.SecurityException> é exibida na janela do console.  
  
 [!code-csharp[DataWorks SqlClient.CAS#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.CAS#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/VB/source.vb#1)]  
  
 Você deverá ver esta saída na janela do console:  
  
```  
Failed, as expected: <IPermission class="System.Data.SqlClient.  
SqlClientPermission, System.Data, Version=2.0.0.0,   
  Culture=neutral, PublicKeyToken=b77a5c561934e089" version="1"  
  AllowBlankPassword="False">  
<add ConnectionString="Data Source=(local);Initial Catalog=  
  Northwind;Integrated Security=SSPI" KeyRestrictions=""  
KeyRestrictionBehavior="AllowOnly"/>  
</IPermission>  
  
Connection opened, as expected.  
Failed, as expected: Request failed.  
```  
  
## <a name="interoperability-with-unmanaged-code"></a>Interoperabilidade com código não gerenciado  
 O código executado fora do CLR é chamado de código não gerenciado. Portanto, mecanismos de segurança, como o CAS, não podem ser aplicados a código não gerenciado. Componentes COM, interfaces ActiveX e funções da API do Win32 são exemplos de código não gerenciado. Aplicam-se considerações de segurança especiais ao executar o código não gerenciado, para que você não coloque em risco a segurança geral do aplicativo. Para obter mais informações, consulte [interoperação com código não gerenciado](../../../../docs/framework/interop/index.md).  
  
 O .NET Framework também oferece suporte à compatibilidade com versões anteriores a componentes COM existentes fornecendo acesso por meio da interoperabilidade COM. Você pode incorporar componentes COM em um aplicativo .NET Framework usando ferramentas de interoperabilidade COM para importar os tipos COM relevantes. Uma vez importados, os tipos COM estão prontos para uso. A interoperabilidade COM também permite que clientes COM acessem o código gerenciado exportando metadados do assembly para uma biblioteca de tipos e registrando o componente gerenciado como um componente COM. Para obter mais informações, consulte [Advanced COM Interoperability](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb).  
  
## <a name="see-also"></a>Consulte também  
 [Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 [PAVE Security in Native and .NET Framework Code](http://msdn.microsoft.com/library/bd61be84-c143-409a-a75a-44253724f784) (PAVE Segurança no código nativo e do .NET Framework)  
 [Segurança de acesso do código](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)  
 [Segurança baseada em Função](http://msdn.microsoft.com/library/239442e3-5be4-4203-b7fd-793baffea803)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
