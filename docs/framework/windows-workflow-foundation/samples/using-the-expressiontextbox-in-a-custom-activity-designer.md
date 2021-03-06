---
title: Usando o ExpressionTextBox em um designer personalizado de atividades
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: ad0c29e2661c82e663fd6b68fdcd74f542ef28b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516780"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>Usando o ExpressionTextBox em um designer personalizado de atividades
Este exemplo mostra como usar <xref:System.Activities.Presentation.View.ExpressionTextBox> em um designer personalizado de atividade. A atividade personalizado, `MultiAssign`, atribui dois valores de cadeia de caracteres a duas variáveis de cadeia de caracteres. Alguns controles de <xref:System.Activities.Presentation.View.ExpressionTextBox> associação a <xref:System.Activities.InArgument>s e associar a qualquer <xref:System.Activities.OutArgument>S.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 `ArgumentToExpressionConverter` é o conversor de tipo usado para associar expressões para argumentos. `ConverterParameter` deve ser definido como `In` ou a `Out` como apropriado. `InOut` não é suportado.  
  
 O `UseLocationExpression` atributo é usado em `OutArgument`s para especificar que a expressão deve ser uma expressão de valor de L ("valor à esquerda" ou "valor local"). Na maioria dos casos, uma expressão de L- valor é um identificador válido Visual Basic usado para indicar que `OutArgument` que está sendo retornado é uma variável ou um nome de argumento.  
  
 O atributo de `MaxLines` é definido como um nesse exemplo e `MinLines` não está definido. Isso indica que <xref:System.Activities.Presentation.View.ExpressionTextBox> é um tamanho fixo de uma linha independentemente da quantidade de texto digitado pelo usuário. Para permitir que <xref:System.Activities.Presentation.View.ExpressionTextBox> venha a entrada do usuário apta, defina `MaxLines` maior do que `MinLines`.  
  
 Um ExpressionTextBox só pode ser associado para argumentos, e não pode ser associado para propriedades de CLR.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de ExpressionTextBoxSample.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
#### <a name="to-run-this-sample"></a>Para executar este exemplo  
  
1.  Adicione um novo aplicativo de console do fluxo de trabalho à solução.  
  
2.  Adicione uma referência para o **ExpressionTextBoxSample** projeto novo projeto de aplicativo de Console do fluxo de trabalho.  
  
3.  Compile a solução.  
  
4.  Arraste o **MultiAssign** atividade da caixa de ferramentas e solte-o no fluxo de trabalho.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Activities.Presentation.View.ExpressionTextBox>  
 [Desenvolvendo aplicativos com o Designer de Fluxo de Trabalho](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
