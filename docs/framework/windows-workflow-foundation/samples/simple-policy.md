---
title: Diretiva simples
ms.date: 03/30/2017
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
ms.openlocfilehash: dff3979d75fdeb5a45be3940af3568c26f5e8f98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515890"
---
# <a name="simple-policy"></a>Diretiva simples
Este exemplo mostra como usar uma atividade de <xref:System.Workflow.Activities.PolicyActivity> em um fluxo de trabalho.  
  
 O fluxo de trabalho sequencial nesse exemplo é criado usando uma atividade de <xref:System.Workflow.Activities.PolicyActivity> . O fluxo de trabalho define `orderValue`, `customerType`, e os campos de `discount` que são usados para definir um fluxo de trabalho de desconto do produto. As regras definidas no arquivo das regras definem um valor de desconto que é baseado em `orderValue` e em `customerType`. `orderValue` e `customerType` são definidos na definição de classe de `SimplePolicyWorkflow` e podem ser modificados para alterar o comportamento. O desconto resultante é escrito no console no manipulador de eventos <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> que é definido na classe de `SimplePolicyWorkflow` .  
  
### <a name="to-build-the-sample"></a>Para criar o exemplo  
  
1.  Abra a solução em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Crie a solução. CTRL+SHIFT+B pressionando.  
  
3.  Executar a solução sem depuração pressionando CTRL + f5.  
  
### <a name="to-run-the-sample"></a>Para executar a amostra  
  
-   Na janela do prompt de comando SDK, execute o arquivo .exe no SimplePolicy \ bin \ debug (ou na pasta \ bin de SimplePolicy para a versão do Visual Basic de exemplo), que está localizado abaixo da pasta principal para o exemplo.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verificar o seguinte diretório (padrão) antes de continuar:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está no seguinte diretório:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [Política avançada](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
