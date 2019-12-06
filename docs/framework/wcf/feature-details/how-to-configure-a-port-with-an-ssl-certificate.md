---
title: HOW TO：使用 SSL 憑證設定連接埠
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: d2fe9a73f79408db08ef48d380940fcf6bb831c0
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837996"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="a0cdc-102">HOW TO：使用 SSL 憑證設定連接埠</span><span class="sxs-lookup"><span data-stu-id="a0cdc-102">How to: Configure a Port with an SSL Certificate</span></span>
<span data-ttu-id="a0cdc-103">使用傳輸安全性的 <xref:System.ServiceModel.WSHttpBinding> 類別建立自我裝載的 Windows Communication Foundation （WCF）服務時，您也必須使用 x.509 憑證設定埠。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-103">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="a0cdc-104">如果您沒有建立自我裝載的服務，可以將您的服務裝載在 Internet Information Services (IIS) 上。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="a0cdc-105">如需詳細資訊，請參閱[HTTP 傳輸安全性](../../../../docs/framework/wcf/feature-details/http-transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-105">For more information, see [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
 <span data-ttu-id="a0cdc-106">若要設定連接埠，使用的工具取決於電腦上執行的作業系統。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="a0cdc-107">如果您是執行 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 或 [!INCLUDE[wxp](../../../../includes/wxp-md.md)]，請使用 HttpCfg.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-107">If you are running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool.</span></span> <span data-ttu-id="a0cdc-108">這個工具會隨 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 進行安裝。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-108">With [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] this tool is installed.</span></span> <span data-ttu-id="a0cdc-109">有了 [!INCLUDE[wxp](../../../../includes/wxp-md.md)]，您可以在[WINDOWS XP Service Pack 2 支援工具](https://go.microsoft.com/fwlink/?LinkId=88606)下載此工具。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-109">With [!INCLUDE[wxp](../../../../includes/wxp-md.md)], you can download the tool at [Windows XP Service Pack 2 Support Tools](https://go.microsoft.com/fwlink/?LinkId=88606).</span></span> <span data-ttu-id="a0cdc-110">如需詳細資訊，請參閱[Httpcfg.exe 總覽](https://go.microsoft.com/fwlink/?LinkId=88605)。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-110">For more information, see [Httpcfg Overview](https://go.microsoft.com/fwlink/?LinkId=88605).</span></span> <span data-ttu-id="a0cdc-111">[Windows 支援工具檔](https://go.microsoft.com/fwlink/?LinkId=94840)會說明 HTTPcfg.exe 工具的語法。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-111">The [Windows Support Tools documentation](https://go.microsoft.com/fwlink/?LinkId=94840) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="a0cdc-112">如果您執行的是 Windows Vista，請使用已安裝的 dism.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-112">If you are running Windows Vista, use the Netsh.exe tool that is already installed.</span></span>  
  
 <span data-ttu-id="a0cdc-113">本主題說明如何完成下列數個程序：</span><span class="sxs-lookup"><span data-stu-id="a0cdc-113">This topic describes how to accomplish several procedures:</span></span>  
  
- <span data-ttu-id="a0cdc-114">判斷電腦目前的連接埠組態。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-114">Determining a computer's current port configuration.</span></span>  
  
- <span data-ttu-id="a0cdc-115">取得憑證的指紋 (如此才能完成下列兩個程序)。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-115">Getting a certificate's thumbprint (necessary for the following two procedures).</span></span>  
  
- <span data-ttu-id="a0cdc-116">將 SSL 憑證繫結至連接埠組態。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-116">Binding an SSL certificate to a port configuration.</span></span>  
  
- <span data-ttu-id="a0cdc-117">將 SSL 憑證繫結至連接埠組態並支援用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-117">Binding an SSL certificate to a port configuration and supporting client certificates.</span></span>  
  
- <span data-ttu-id="a0cdc-118">從連接埠號碼刪除 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-118">Deleting an SSL certificate from a port number.</span></span>  
  
 <span data-ttu-id="a0cdc-119">請注意，您必須具備系統管理員權限，才能修改儲存在電腦上的憑證。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-119">Note that modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
### <a name="to-determine-how-ports-are-configured"></a><span data-ttu-id="a0cdc-120">決定如何設定連接埠</span><span class="sxs-lookup"><span data-stu-id="a0cdc-120">To determine how ports are configured</span></span>  
  
1. <span data-ttu-id="a0cdc-121">在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 或 [!INCLUDE[wxp](../../../../includes/wxp-md.md)]中，使用 Httpcfg.exe 工具來查看目前的埠設定，其方式是使用**查詢**和**ssl**參數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-121">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="a0cdc-122">在 Windows Vista 中，使用 Netsh 工具來查看目前的埠設定，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-122">In Windows Vista, use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a><span data-ttu-id="a0cdc-123">若要取得憑證的指紋</span><span class="sxs-lookup"><span data-stu-id="a0cdc-123">To get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="a0cdc-124">使用憑證 MMC 嵌入式管理單元，尋找目的為用戶端驗證的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-124">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="a0cdc-125">如需詳細資訊，請參閱[如何：使用 MMC 嵌入式管理單元來檢視憑證](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-125">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="a0cdc-126">存取憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-126">Access the certificate's thumbprint.</span></span> <span data-ttu-id="a0cdc-127">如需詳細資訊，請參閱[做法：擷取憑證的指紋](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-127">For more information, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="a0cdc-128">將憑證的指紋複製到文字編輯器中，例如「記事本」。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-128">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="a0cdc-129">移除十六進位字元之間的所有空格。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-129">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="a0cdc-130">完成這項工作的方法之一是使用文字編輯器的尋找與取代功能，並使用 null 字元來取代各個空格。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-130">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="a0cdc-131">繫結 SSL 憑證與連接埠號碼</span><span class="sxs-lookup"><span data-stu-id="a0cdc-131">To bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="a0cdc-132">在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 或 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 中，在 Secure Sockets Layer (SSL) 存放區上的 "set" 模式中使用 HttpCfg.exe 工具，將憑證繫結至連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-132">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="a0cdc-133">此工具是使用指紋來識別憑證，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-133">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="a0cdc-134">**-I**參數具有 `IP`：`port` 的語法，並指示工具將憑證設定為電腦的埠8012。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-134">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="a0cdc-135">或者，號碼前面的四個零也可以使用電腦的實際 IP 位址來取代。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-135">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="a0cdc-136">**-H**參數會指定憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-136">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="a0cdc-137">在 Windows Vista 中，請使用 Netsh 工具，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-137">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    - <span data-ttu-id="a0cdc-138">**Certhash**參數會指定憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-138">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="a0cdc-139">**Ipport**參數會指定 IP 位址和埠，而函式就如同所述的 HTTPcfg.exe .exe 工具的 **-i**參數。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-139">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="a0cdc-140">**Appid**參數是可以用來識別擁有應用程式的 GUID。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-140">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="a0cdc-141">繫結 SSL 憑證與連接埠號碼並支援用戶端憑證</span><span class="sxs-lookup"><span data-stu-id="a0cdc-141">To bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="a0cdc-142">在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 或 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 中，若要支援在傳輸層使用 X.509 憑證驗證的用戶端，請依照前述程序執行，但將額外的命令列參數傳遞至 HttpCfg.exe，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-142">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="a0cdc-143">**-F**參數具有 `n` 的語法，其中 n 是介於1和7之間的數位。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-143">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="a0cdc-144">值為 2 (如上一個範例所示) 會在傳輸層啟用用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-144">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="a0cdc-145">值為 3 會啟用用戶端憑證，並將這些憑證對應至 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-145">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="a0cdc-146">如需其他值的行為，請參閱 HttpCfg.exe 說明。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-146">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="a0cdc-147">在 Windows Vista 中，若要支援在傳輸層使用 x.509 憑證進行驗證的用戶端，請遵循先前的程式，但使用其他參數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-147">In Windows Vista, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="a0cdc-148">從連接埠號碼刪除 SSL 憑證</span><span class="sxs-lookup"><span data-stu-id="a0cdc-148">To delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="a0cdc-149">使用 HttpCfg.exe 或 Netsh.exe 工具來查看電腦上所有繫結的連接埠和指紋。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-149">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="a0cdc-150">若要將資訊列印到磁片，請使用重新導向字元 ">"，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-150">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="a0cdc-151">在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 或 [!INCLUDE[wxp](../../../../includes/wxp-md.md)]中，使用 Httpcfg.exe 工具搭配**delete**和**ssl**關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-151">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="a0cdc-152">使用 **-i**參數指定 `IP`：`port` 號碼，而 **-h**參數用來指定指紋。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-152">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="a0cdc-153">在 Windows Vista 中，請使用 Netsh 工具，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-153">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="a0cdc-154">範例</span><span class="sxs-lookup"><span data-stu-id="a0cdc-154">Example</span></span>  
 <span data-ttu-id="a0cdc-155">下列程式碼將示範如何使用設定為傳輸安全性的 <xref:System.ServiceModel.WSHttpBinding> 類別來建立自我裝載的服務。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-155">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="a0cdc-156">當建立應用程式時，請在位址中指定連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="a0cdc-156">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a0cdc-157">請參閱</span><span class="sxs-lookup"><span data-stu-id="a0cdc-157">See also</span></span>

- [<span data-ttu-id="a0cdc-158">HTTP 傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="a0cdc-158">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
