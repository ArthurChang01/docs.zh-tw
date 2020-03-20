---
title: 強式命名 (Unmanaged API 參考)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
ms.openlocfilehash: 7d18513450111d58b5d26fd834addd465cfc4267
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140640"
---
# <a name="strong-naming-unmanaged-api-reference"></a><span data-ttu-id="57c6e-102">強式命名 (Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="57c6e-102">Strong Naming (Unmanaged API Reference)</span></span>
<span data-ttu-id="57c6e-103">強式命名 API 可讓用戶端管理組件的強式命名簽署。</span><span class="sxs-lookup"><span data-stu-id="57c6e-103">The strong naming API enables a client to administer strong name signing for assemblies.</span></span>  
  
 <span data-ttu-id="57c6e-104">使用強式名稱簽署組件，就會將公開金鑰加密加入含有組件資訊清單的檔案中。</span><span class="sxs-lookup"><span data-stu-id="57c6e-104">Signing an assembly with a strong name adds a public key encryption to the file containing the assembly manifest.</span></span> <span data-ttu-id="57c6e-105">強式名稱簽署可協助驗證名稱唯一性，防止名稱冒用，並且在解析參考時為呼叫者提供唯一身分識別。</span><span class="sxs-lookup"><span data-stu-id="57c6e-105">Strong name signing helps verify name uniqueness, prevents name spoofing, and provides callers with a unique identity when a reference is resolved.</span></span> <span data-ttu-id="57c6e-106">但是，並沒有任何信任等級與強式名稱關聯。</span><span class="sxs-lookup"><span data-stu-id="57c6e-106">However, no level of trust is associated with a strong name.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="57c6e-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="57c6e-107">In This Section</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57c6e-108">從 .NET Framework 4 開始，所有這些函式都已過時。</span><span class="sxs-lookup"><span data-stu-id="57c6e-108">All of these functions have been deprecated starting with the .NET Framework 4.</span></span> <span data-ttu-id="57c6e-109">如需建議的替代函式，請參閱 [ICLRStrongName](../hosting/iclrstrongname-interface.md) 介面。</span><span class="sxs-lookup"><span data-stu-id="57c6e-109">For suggested alternatives, see the [ICLRStrongName](../hosting/iclrstrongname-interface.md) interface.</span></span>  
  
 [<span data-ttu-id="57c6e-110">GetHashFromAssemblyFile 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-110">GetHashFromAssemblyFile Function</span></span>](gethashfromassemblyfile-function.md)  
 <span data-ttu-id="57c6e-111">使用指定的雜湊演算法取得所指定組件檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="57c6e-111">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="57c6e-112">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-112">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-113">GetHashFromAssemblyFileW 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-113">GetHashFromAssemblyFileW Function</span></span>](gethashfromassemblyfilew-function.md)  
 <span data-ttu-id="57c6e-114">使用指定的雜湊演算法取得以 Unicode 字串形式指定的組件檔案雜湊。</span><span class="sxs-lookup"><span data-stu-id="57c6e-114">Gets a hash of the assembly file specified as a Unicode string, using the specified hash algorithm.</span></span> <span data-ttu-id="57c6e-115">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-115">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-116">GetHashFromBlob 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-116">GetHashFromBlob Function</span></span>](gethashfromblob-function.md)  
 <span data-ttu-id="57c6e-117">使用指定的雜湊演算法取得位於指定記憶體位址之組件的雜湊。</span><span class="sxs-lookup"><span data-stu-id="57c6e-117">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span> <span data-ttu-id="57c6e-118">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-118">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-119">GetHashFromFile 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-119">GetHashFromFile Function</span></span>](gethashfromfile-function.md)  
 <span data-ttu-id="57c6e-120">產生指定檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="57c6e-120">Generates a hash over the contents of the specified file.</span></span>  <span data-ttu-id="57c6e-121">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-121">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-122">GetHashFromFileW 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-122">GetHashFromFileW Function</span></span>](gethashfromfilew-function.md)  
 <span data-ttu-id="57c6e-123">產生以 Unicode 字串指定之檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="57c6e-123">Generates a hash over the contents of the file specified by a Unicode string.</span></span> <span data-ttu-id="57c6e-124">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-124">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-125">GetHashFromHandle 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-125">GetHashFromHandle Function</span></span>](gethashfromhandle-function.md)  
 <span data-ttu-id="57c6e-126">使用指定的雜湊演算法產生以指定檔案控制代碼指定之檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="57c6e-126">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  <span data-ttu-id="57c6e-127">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-127">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-128">StrongNameCompareAssemblies 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-128">StrongNameCompareAssemblies Function</span></span>](strongnamecompareassemblies-function.md)  
 <span data-ttu-id="57c6e-129">判斷兩個組件是否只有強制名稱簽章不同。</span><span class="sxs-lookup"><span data-stu-id="57c6e-129">Determines whether two assemblies differ only by their strong name signatures.</span></span> <span data-ttu-id="57c6e-130">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-130">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-131">StrongNameErrorInfo 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-131">StrongNameErrorInfo Function</span></span>](strongnameerrorinfo-function.md)  
 <span data-ttu-id="57c6e-132">取得由其中一強式名稱函式所引發的最後一個錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="57c6e-132">Gets the last error code that was raised by one of the strong name functions.</span></span>  
  
 [<span data-ttu-id="57c6e-133">StrongNameFreeBuffer 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-133">StrongNameFreeBuffer Function</span></span>](strongnamefreebuffer-function.md)  
 <span data-ttu-id="57c6e-134">釋放使用對強式名稱函式 (例如 [StrongNameGetPublicKey](strongnamegetpublickey-function.md)、[StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md) 或 [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)) 的上一個呼叫所配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="57c6e-134">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>   <span data-ttu-id="57c6e-135">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-135">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-136">StrongNameGetBlob 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-136">StrongNameGetBlob Function</span></span>](strongnamegetblob-function.md)  
 <span data-ttu-id="57c6e-137">使用位於所指定位址之可執行檔的二進位表示法填滿指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="57c6e-137">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span> <span data-ttu-id="57c6e-138">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-138">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-139">StrongNameGetBlobFromImage 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-139">StrongNameGetBlobFromImage Function</span></span>](strongnamegetblobfromimage-function.md)  
 <span data-ttu-id="57c6e-140">取得位於所指定記憶體位置之組件影像的二進位表示法。</span><span class="sxs-lookup"><span data-stu-id="57c6e-140">Gets a binary representation of the assembly image at the specified memory address.</span></span> <span data-ttu-id="57c6e-141">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-141">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-142">StrongNameGetPublicKey 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-142">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)  
 <span data-ttu-id="57c6e-143">從私密/公開金鑰組取得公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-143">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="57c6e-144">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-144">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-145">StrongNameHashSize 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-145">StrongNameHashSize Function</span></span>](strongnamehashsize-function.md)  
 <span data-ttu-id="57c6e-146">使用指定的雜湊演算法取得雜湊所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="57c6e-146">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  <span data-ttu-id="57c6e-147">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-147">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-148">StrongNameKeyDelete 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-148">StrongNameKeyDelete Function</span></span>](strongnamekeydelete-function.md)  
 <span data-ttu-id="57c6e-149">刪除指定的金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="57c6e-149">Deletes the specified key container.</span></span> <span data-ttu-id="57c6e-150">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-150">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-151">StrongNameKeyGen 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-151">StrongNameKeyGen Function</span></span>](strongnamekeygen-function.md)  
 <span data-ttu-id="57c6e-152">建立將供強式名稱使用的新公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="57c6e-152">Creates a new public/private key pair for strong name use.</span></span>  <span data-ttu-id="57c6e-153">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-153">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-154">StrongNameKeyGenEx 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-154">StrongNameKeyGenEx Function</span></span>](strongnamekeygenex-function.md)  
 <span data-ttu-id="57c6e-155">使用指定的金鑰大小產生將供強式名稱使用的新公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="57c6e-155">Generates a new public/private key pair with the specified key size for strong name use.</span></span> <span data-ttu-id="57c6e-156">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-156">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-157">StrongNameKeyInstall 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-157">StrongNameKeyInstall Function</span></span>](strongnamekeyinstall-function.md)  
 <span data-ttu-id="57c6e-158">將公開/私密金鑰組匯入到容器中。</span><span class="sxs-lookup"><span data-stu-id="57c6e-158">Imports a public/private key pair into a container.</span></span>  <span data-ttu-id="57c6e-159">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-159">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-160">StrongNameSignatureGeneration 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-160">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)  
 <span data-ttu-id="57c6e-161">產生指定組件的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="57c6e-161">Generates a strong name signature for the specified assembly.</span></span>   <span data-ttu-id="57c6e-162">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-162">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-163">StrongNameSignatureGenerationEx 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-163">StrongNameSignatureGenerationEx Function</span></span>](strongnamesignaturegenerationex-function.md)  
 <span data-ttu-id="57c6e-164">以指定的旗標為基礎產生指定組件的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="57c6e-164">Generates a strong name signature for the specified assembly, based on the specified flags.</span></span>    <span data-ttu-id="57c6e-165">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-165">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-166">StrongNameSignatureSize 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-166">StrongNameSignatureSize Function</span></span>](strongnamesignaturesize-function.md)  
 <span data-ttu-id="57c6e-167">傳回強式名稱簽章的大小。</span><span class="sxs-lookup"><span data-stu-id="57c6e-167">Returns the size of the strong name signature.</span></span> <span data-ttu-id="57c6e-168">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-168">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-169">StrongNameSignatureVerification 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-169">StrongNameSignatureVerification Function</span></span>](strongnamesignatureverification-function.md)  
 <span data-ttu-id="57c6e-170">取得指出位於所指定路徑之組件資訊清單是否包含強式名稱簽章的值 (會根據指定的旗標驗證此值)。</span><span class="sxs-lookup"><span data-stu-id="57c6e-170">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span> <span data-ttu-id="57c6e-171">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-171">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-172">StrongNameSignatureVerificationEx 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-172">StrongNameSignatureVerificationEx Function</span></span>](strongnamesignatureverificationex-function.md)  
 <span data-ttu-id="57c6e-173">取得指出位於指定路徑的組件資訊清單是否包含強式名稱簽章的值。</span><span class="sxs-lookup"><span data-stu-id="57c6e-173">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  <span data-ttu-id="57c6e-174">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-174">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-175">StrongNameSignatureVerificationFromImage 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-175">StrongNameSignatureVerificationFromImage Function</span></span>](strongnamesignatureverificationfromimage-function.md)  
 <span data-ttu-id="57c6e-176">驗證已對應到記憶體的組件對關聯的公開金鑰而言有效。</span><span class="sxs-lookup"><span data-stu-id="57c6e-176">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span> <span data-ttu-id="57c6e-177">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-177">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-178">StrongNameTokenFromAssembly 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-178">StrongNameTokenFromAssembly Function</span></span>](strongnametokenfromassembly-function.md)  
 <span data-ttu-id="57c6e-179">從指定的組件檔案建立強式名稱權杖。</span><span class="sxs-lookup"><span data-stu-id="57c6e-179">Creates a strong name token from the specified assembly file.</span></span>  <span data-ttu-id="57c6e-180">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-180">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-181">StrongNameTokenFromAssemblyEx 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-181">StrongNameTokenFromAssemblyEx Function</span></span>](strongnametokenfromassemblyex-function.md)  
 <span data-ttu-id="57c6e-182">從指定組件檔案建立強式名稱權杖，並傳回公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-182">Creates a strong name token from the specified assembly file, and returns the public key.</span></span> <span data-ttu-id="57c6e-183">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-183">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-184">StrongNameTokenFromPublicKey 函式</span><span class="sxs-lookup"><span data-stu-id="57c6e-184">StrongNameTokenFromPublicKey Function</span></span>](strongnametokenfrompublickey-function.md)  
 <span data-ttu-id="57c6e-185">取得代表公開金鑰的權杖。</span><span class="sxs-lookup"><span data-stu-id="57c6e-185">Gets a token representing a public key.</span></span> <span data-ttu-id="57c6e-186">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="57c6e-186">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="57c6e-187">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="57c6e-187">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)  
 <span data-ttu-id="57c6e-188">代表公開/私密金鑰組的公開金鑰 (二進位格式)。</span><span class="sxs-lookup"><span data-stu-id="57c6e-188">Represents the public key of a public/private key pair in binary format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57c6e-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57c6e-189">See also</span></span>

- [<span data-ttu-id="57c6e-190">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="57c6e-190">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="57c6e-191">非託管 API 引用</span><span class="sxs-lookup"><span data-stu-id="57c6e-191">Unmanaged API Reference</span></span>](../index.md)
