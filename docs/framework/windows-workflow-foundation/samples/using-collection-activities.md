---
title: Usando atividades de coleção
ms.date: 03/30/2017
ms.assetid: e1977cf8-1695-4071-b946-7046fe39601e
ms.openlocfilehash: 3c30a7fb46d9b155ec645a7b6845715d808d63b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516588"
---
# <a name="using-collection-activities"></a>Usando atividades de coleção
Este exemplo demonstra como usar as atividades de coleção (<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601>, e <xref:System.Activities.Statements.RemoveFromCollection%601>) com uma classe que implementa a interface de <xref:System.Collections.ICollection> e como criar uma atividade personalizado que executa iterações sobre uma coleção para imprimir para fora o conteúdo de cada elemento na coleção. A atividade personalizado, que é chamada `PrintCollection`, imprime no console os membros do item de uma coleção chamada `Numbers`.  
  
 A tabela a seguir descreve as quatro atividades que fornecem a manipulação de coleção para fluxos de trabalho.  
  
|Nome de atividade|Descrição|  
|-------------------|-----------------|  
|<xref:System.Activities.Statements.AddToCollection%601>|Adiciona um item a uma coleção.|  
|<xref:System.Activities.Statements.ClearCollection%601>|Limpa todos os itens em uma coleção|  
|<xref:System.Activities.Statements.ExistsInCollection%601>|Retorna `true` se o item especificado existe na coleção.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601>|Remove um item de uma coleção.|  
  
 O exemplo consiste duas soluções, uma no diretório de CodedWorkflow e a outra no diretório de DesignerWorkflow. Demonstram duas maneiras diferentes de usar as atividades para as mesmas fins.  
  
|Solução|Descrição|Arquivos de chave|  
|-|-|-|  
|CodedWorkflow|Exemplo do aplicativo cliente que demonstra como chamar programaticamente as atividades de coleção.|**PrintCollection.cs**: atividade de auxiliar para imprimir para o console de cada item em uma coleção.<br /><br /> **Program.CS**: cria programaticamente uma atividade de sequência que contém uma série de atividades de coleção e o executa.|  
|DesignerWorkflow|Exemplo do aplicativo cliente que demonstra como usar declarativamente as atividades de coleção no designer de fluxo de trabalho.|**CollectionWorkflow.xaml**: um fluxo de trabalho criado declarativamente com o designer que usa as atividades de coleção.<br /><br /> **PrintCollection.cs**: atividade de auxiliar para imprimir para o console de cada item em uma coleção.<br /><br /> **Program.CS**: invoca o fluxo de trabalho descrito em CollectionWorkflow.xaml.|  
  
 Em demonstração, os membros do item da coleção `Numbers` será impresso no console usando uma atividade de chamada definida `PrintCollection`.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de Collection.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Collection`