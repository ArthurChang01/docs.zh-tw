---
title: 已知型別
ms.date: 03/30/2017
ms.assetid: 88d83720-ca38-4b2c-86a6-f149ed1d89ec
ms.openlocfilehash: b75f540694eaeea90367f1720d5747f71d0a392d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144613"
---
# <a name="known-types"></a><span data-ttu-id="5c57c-102">已知型別</span><span class="sxs-lookup"><span data-stu-id="5c57c-102">Known Types</span></span>
<span data-ttu-id="5c57c-103">這個範例會示範如何在資料合約中指定有關衍生型別的資訊。</span><span class="sxs-lookup"><span data-stu-id="5c57c-103">This sample demonstrates how to specify information about derived types in a data contract.</span></span> <span data-ttu-id="5c57c-104">資料合約可以讓您在服務間來回傳遞結構化資料。</span><span class="sxs-lookup"><span data-stu-id="5c57c-104">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="5c57c-105">在物件導向程式設計中，繼承自另一個型別的型別可以用來取代原始型別。</span><span class="sxs-lookup"><span data-stu-id="5c57c-105">In object-oriented programming, a type that inherits from another type can be used in place of the original type.</span></span> <span data-ttu-id="5c57c-106">在服務導向程式設計中，會使用結構描述而不是型別進行通訊，因此不會保留型別之間的關係。</span><span class="sxs-lookup"><span data-stu-id="5c57c-106">In service-oriented programming, schemas rather than types are communicated and therefore, the relationship between types is not preserved.</span></span> <span data-ttu-id="5c57c-107"><xref:System.Runtime.Serialization.KnownTypeAttribute> 屬性可以讓關於衍生型別的資訊包含到資料合約中。</span><span class="sxs-lookup"><span data-stu-id="5c57c-107">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute allows information about derived types to be included in the data contract.</span></span> <span data-ttu-id="5c57c-108">如果不使用這個機制，這時將無法傳送或接收衍生型別，因為預期是使用基底型別 (Base Type)。</span><span class="sxs-lookup"><span data-stu-id="5c57c-108">If this mechanism is not used, a derived type cannot be sent or received where a base type is expected.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c57c-109">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="5c57c-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5c57c-110">此服務的服務合約會使用複數，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="5c57c-110">The service contract for the service uses complex numbers, as shown in the following sample code.</span></span>  
  
```csharp
// Define a service contract.  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    ComplexNumber Add(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2);  
}  
```  
  
 <span data-ttu-id="5c57c-111"><xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 會套用至 `ComplexNumber` 類別，以便指示可在用戶端與服務之間傳遞的類別欄位。</span><span class="sxs-lookup"><span data-stu-id="5c57c-111">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> is applied to the `ComplexNumber` class to indicate which fields of the class can be passed between the client and the service.</span></span> <span data-ttu-id="5c57c-112">衍生的 `ComplexNumberWithMagnitude` 類別可以用來取代 `ComplexNumber`。</span><span class="sxs-lookup"><span data-stu-id="5c57c-112">The derived `ComplexNumberWithMagnitude` class can be used in place of `ComplexNumber`.</span></span> <span data-ttu-id="5c57c-113"><xref:System.Runtime.Serialization.KnownTypeAttribute> 型別的 `ComplexNumber` 屬性會指示這項資訊。</span><span class="sxs-lookup"><span data-stu-id="5c57c-113">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute on the `ComplexNumber` type indicates this.</span></span>  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
[KnownType(typeof(ComplexNumberWithMagnitude))]  
public class ComplexNumber  
{  
    [DataMember]  
    public double Real = 0.0D;  
    [DataMember]  
    public double Imaginary = 0.0D;  
  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
 <span data-ttu-id="5c57c-114">`ComplexNumberWithMagnitude` 型別衍生自 `ComplexNumber`，但是其新增額外的資料成員，`Magnitude`。</span><span class="sxs-lookup"><span data-stu-id="5c57c-114">The `ComplexNumberWithMagnitude` type derives from `ComplexNumber` but adds an additional data member, `Magnitude`.</span></span>  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class ComplexNumberWithMagnitude : ComplexNumber  
{  
    public ComplexNumberWithMagnitude(double real, double imaginary) :  
        base(real, imaginary) { }  
  
    [DataMember]  
    public double Magnitude  
    {  
        get { return Math.Sqrt(Imaginary*Imaginary  + Real*Real); }  
        set { throw new NotImplementedException(); }  
    }  
}  
```  
  
 <span data-ttu-id="5c57c-115">為了演示已知類型功能，服務的實現方式使其僅返回添加`ComplexNumberWithMagnitude`和減法。</span><span class="sxs-lookup"><span data-stu-id="5c57c-115">To demonstrate the known types feature, the service is implemented in such a way that it returns a `ComplexNumberWithMagnitude` only for addition and subtraction.</span></span> <span data-ttu-id="5c57c-116">(雖然合約會指定 `ComplexNumber`，但是因為 `KnownTypeAttribute` 屬性的關係，所以仍會允許這項行為)。</span><span class="sxs-lookup"><span data-stu-id="5c57c-116">(Even though the contract specifies `ComplexNumber`, this is allowed because of the `KnownTypeAttribute` attribute).</span></span> <span data-ttu-id="5c57c-117">乘法和除法仍返回基`ComplexNumber`類型。</span><span class="sxs-lookup"><span data-stu-id="5c57c-117">Multiplication and division still return the base `ComplexNumber` type.</span></span>  
  
```csharp
public class DataContractCalculatorService : IDataContractCalculator  
{  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        //Return the derived type.  
        return new ComplexNumberWithMagnitude(n1.Real + n2.Real,  
                                      n1.Imaginary + n2.Imaginary);  
    }  
  
    public ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2)  
    {  
        //Return the derived type.  
        return new ComplexNumberWithMagnitude(n1.Real - n2.Real,
                                 n1.Imaginary - n2.Imaginary);  
    }  
  
    public ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2)  
    {  
        double real1 = n1.Real * n2.Real;  
        double imaginary1 = n1.Real * n2.Imaginary;  
        double imaginary2 = n2.Real * n1.Imaginary;  
        double real2 = n1.Imaginary * n2.Imaginary * -1;  
        //Return the base type.  
        return new ComplexNumber(real1 + real2, imaginary1 +
                                                  imaginary2);  
    }  
  
    public ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2)  
    {  
        ComplexNumber conjugate = new ComplexNumber(n2.Real,
                                     -1*n2.Imaginary);  
        ComplexNumber numerator = Multiply(n1, conjugate);  
        ComplexNumber denominator = Multiply(n2, conjugate);  
        //Return the base type.  
        return new ComplexNumber(numerator.Real / denominator.Real,  
                                             numerator.Imaginary);  
    }  
}  
```  
  
 <span data-ttu-id="5c57c-118">在用戶端上，服務協定和資料協定都generatedClient.cs原始檔案中定義，該檔由[服務模型中繼資料實用程式工具 （Svcutil.exe）](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)從服務中繼資料生成。</span><span class="sxs-lookup"><span data-stu-id="5c57c-118">On the client, both the service contract and the data contract are defined in the source file generatedClient.cs, which is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span> <span data-ttu-id="5c57c-119">因為服務資料合約中是指定 <xref:System.Runtime.Serialization.KnownTypeAttribute> 屬性，所以用戶端在使用服務時便能夠同時接收 `ComplexNumber` 和 `ComplexNumberWithMagnitude` 類別。</span><span class="sxs-lookup"><span data-stu-id="5c57c-119">Because the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute is specified in the service's data contract, the client is able to receive both the `ComplexNumber` and `ComplexNumberWithMagnitude` classes when using the service.</span></span> <span data-ttu-id="5c57c-120">用戶端會偵測其是否收到 `ComplexNumberWithMagnitude`，然後產生適當的輸出：</span><span class="sxs-lookup"><span data-stu-id="5c57c-120">The client detects whether it got a `ComplexNumberWithMagnitude` and generate the appropriate output:</span></span>  
  
```csharp
// Create a client  
DataContractCalculatorClient client =
    new DataContractCalculatorClient();  
  
// Call the Add service operation.  
ComplexNumber value1 = new ComplexNumber() { real = 1, imaginary = 2 };  
ComplexNumber value2 = new ComplexNumber() { real = 3, imaginary = 4 };  
ComplexNumber result = client.Add(value1, value2);  
Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
    value1.real, value1.imaginary, value2.real, value2.imaginary,  
    result.real, result.imaginary);  
if (result is ComplexNumberWithMagnitude)  
{  
    Console.WriteLine("Magnitude: {0}",
        ((ComplexNumberWithMagnitude)result).Magnitude);  
}  
else  
{  
    Console.WriteLine("No magnitude was sent from the service");  
}  
```  
  
 <span data-ttu-id="5c57c-121">當您執行範例時，作業的要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="5c57c-121">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="5c57c-122">請注意，此服務的實作方式會使得加法與減法列印值範圍，但是乘法與除法則不會列印。</span><span class="sxs-lookup"><span data-stu-id="5c57c-122">Note that a magnitude is printed for addition and subtraction but not for multiplication and division because of the way the service was implemented.</span></span> <span data-ttu-id="5c57c-123">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="5c57c-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Magnitude: 7.21110255092798  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Magnitude: 2.82842712474619  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
No magnitude was sent from the service  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 41i  
No magnitude was sent from the service  
  
    Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5c57c-124">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="5c57c-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5c57c-125">確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="5c57c-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5c57c-126">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="5c57c-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5c57c-127">要在單機或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。</span><span class="sxs-lookup"><span data-stu-id="5c57c-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5c57c-128">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="5c57c-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5c57c-129">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="5c57c-129">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5c57c-130">如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="5c57c-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5c57c-131">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="5c57c-131">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\KnownTypes`  
