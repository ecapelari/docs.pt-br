---
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: 0aba43524dba99b8ae2f63dca9babbb8c3438f4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33503230"
---
# <a name="datacontractresolver"></a>DataContractResolver
Este exemplo demonstra como os processos de serialização e desserialização podem ser personalizados usando o <xref:System.Runtime.Serialization.DataContractResolver> classe. Este exemplo mostra como usar um DataContractResolver para mapear tipos CLR para e de uma representação de xsi: Type durante a serialização e desserialização.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 O exemplo define os seguintes tipos CLR.  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
  
namespace Types  
{  
    [DataContract]  
    public class Customer  
    {  
        [DataMember]  
        public string Name { get; set; }  
    }  
  
    [DataContract]  
    public class VIPCustomer : Customer  
    {  
        [DataMember]  
        public string VipInfo { get; set; }  
    }  
  
    [DataContract]  
    public class RegularCustomer : Customer  
    {  
    }  
  
    [DataContract]  
    public class PreferredVIPCustomer : VIPCustomer  
    {  
    }  
}  
```  
  
 O exemplo carrega o assembly, extrai cada um desses tipos e, em seguida, serializa e desserializa-los. O <xref:System.Runtime.Serialization.DataContractResolver> está conectado ao processo de serialização, passando uma instância do <xref:System.Runtime.Serialization.DataContractResolver>-derivado da classe para o <xref:System.Runtime.Serialization.DataContractSerializer> construtor, conforme mostrado no exemplo a seguir.  
  
```csharp  
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));  
```  
  
 O exemplo, em seguida, serializa os tipos CLR, conforme mostrado no exemplo de código a seguir.  
  
```csharp  
Assembly assembly = Assembly.Load(new AssemblyName("Types"));  
  
public void serialize(Type type)  
{  
    Object instance = Activator.CreateInstance(type);  
  
    Console.WriteLine("----------------------------------------");  
    Console.WriteLine();  
    Console.WriteLine("Serializing type: {0}", type.Name);  
    Console.WriteLine();  
    this.buffer = new StringBuilder();  
    using (XmlWriter xmlWriter = XmlWriter.Create(this.buffer))  
    {  
        try  
        {  
            this.serializer.WriteObject(xmlWriter, instance);  
        }  
        catch (SerializationException error)  
        {  
            Console.WriteLine(error.ToString());  
        }  
    }  
    Console.WriteLine(this.buffer.ToString());  
}  
```  
  
 O exemplo, em seguida, desserializa o xsi:types, conforme mostrado no exemplo de código a seguir.  
  
```csharp  
public void deserialize(Type type)  
{  
    Console.WriteLine();  
    Console.WriteLine("Deserializing type: {0}", type.Name);  
    Console.WriteLine();  
    using (XmlReader xmlReader = XmlReader.Create(new StringReader(this.buffer.ToString())))  
    {  
        Object obj = this.serializer.ReadObject(xmlReader);  
    }  
}  
```  
  
 Desde personalizado <xref:System.Runtime.Serialization.DataContractResolver> é passada para o <xref:System.Runtime.Serialization.DataContractSerializer> construtor, o <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> é chamado durante a serialização para mapear um tipo CLR para um equivalente `xsi:type`. Da mesma forma a <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> é chamado durante a desserialização para mapear o `xsi:type` para um tipo CLR equivalente. Neste exemplo, o <xref:System.Runtime.Serialization.DataContractResolver> é definido como mostrado no exemplo a seguir.  
  
 O exemplo de código a seguir é uma classe derivando de <xref:System.Runtime.Serialization.DataContractResolver>.  
  
```  
class MyDataContractResolver : DataContractResolver  
{  
    private Dictionary<string, XmlDictionaryString> dictionary = new Dictionary<string, XmlDictionaryString>();  
    Assembly assembly;  
  
    public MyDataContractResolver(Assembly assembly)  
    {  
        this.assembly = assembly;  
    }  
  
    // Used at deserialization  
    // Allows users to map xsi:type name to any Type   
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
    {  
        XmlDictionaryString tName;  
        XmlDictionaryString tNamespace;  
        if (dictionary.TryGetValue(typeName, out tName) && dictionary.TryGetValue(typeNamespace, out tNamespace))  
        {  
            return this.assembly.GetType(tNamespace.Value + "." + tName.Value);  
        }  
        else  
        {  
            return null;  
        }  
    }  
  
    // Used at serialization  
    // Maps any Type to a new xsi:type representation  
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
    {  
        string name = dataContractType.Name;  
        string namesp = dataContractType.Namespace;  
        typeName = new XmlDictionaryString(XmlDictionary.Empty, name, 0);   
        typeNamespace = new XmlDictionaryString(XmlDictionary.Empty, namesp, 0);  
        if (!dictionary.ContainsKey(dataContractType.Name))  
        {  
            dictionary.Add(name, typeName);  
        }  
        if (!dictionary.ContainsKey(dataContractType.Namespace))  
        {  
            dictionary.Add(namesp, typeNamespace);  
        }  
    }  
}  
```  
  
 Como parte do exemplo, o projeto de tipos gera o assembly com todos os tipos que são usados neste exemplo. Use este projeto para adicionar, remover ou modificar os tipos que serão serializados.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo de solução de DCRSample.sln.  
  
2.  Para executar a solução, pressione F5  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a>Consulte também  
 [Usar um resolvedor de contrato de dados](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
