---
title: 序列化程序中的步驟
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: f30dd550437e6bc1030c79865bf2edd2c0efbfa9
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741046"
---
# <a name="steps-in-the-serialization-process"></a><span data-ttu-id="16dcb-102">序列化程序中的步驟</span><span class="sxs-lookup"><span data-stu-id="16dcb-102">Steps in the serialization process</span></span>
<span data-ttu-id="16dcb-103">在[格式子](xref:System.Runtime.Serialization.Formatter)上呼叫 <xref:System.Runtime.Serialization.Formatter.Serialize%2A> 方法時，物件序列化會遵循下列規則順序繼續進行：</span><span class="sxs-lookup"><span data-stu-id="16dcb-103">When the <xref:System.Runtime.Serialization.Formatter.Serialize%2A> method is called on a [formatter](xref:System.Runtime.Serialization.Formatter), object serialization proceeds according to the following sequence of rules:</span></span>

- <span data-ttu-id="16dcb-104">進行檢查以判斷格式子是否有代理選取器。</span><span class="sxs-lookup"><span data-stu-id="16dcb-104">A check is made to determine whether the formatter has a surrogate selector.</span></span> <span data-ttu-id="16dcb-105">若格式子有代理選取器，檢查代理選取器是否處理指定型別的物件。</span><span class="sxs-lookup"><span data-stu-id="16dcb-105">If the formatter does, check whether the surrogate selector handles objects of the given type.</span></span> <span data-ttu-id="16dcb-106">若選取器可處理物件類型，會對代理選取器呼叫 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="16dcb-106">If the selector handles the object type, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> is called on the surrogate selector.</span></span>

- <span data-ttu-id="16dcb-107">若無代理選取器，或它不處理物件類型，則檢查以判斷物件是否以 [Serializable](xref:System.SerializableAttribute) 屬性標記。</span><span class="sxs-lookup"><span data-stu-id="16dcb-107">If there is no surrogate selector or if it does not handle the object type, a check is made to determine whether the object is marked with the [Serializable](xref:System.SerializableAttribute) attribute.</span></span> <span data-ttu-id="16dcb-108">如果物件不是，就會擲回 <xref:System.Runtime.Serialization.SerializationException>。</span><span class="sxs-lookup"><span data-stu-id="16dcb-108">If the object is not, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>

- <span data-ttu-id="16dcb-109">若物件有適當地標記，檢查物件是否實作 <xref:System.Runtime.Serialization.ISerializable> 介面。</span><span class="sxs-lookup"><span data-stu-id="16dcb-109">If the object is marked appropriately, check whether the object implements the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="16dcb-110">若物件實作，會對物件呼叫 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>。</span><span class="sxs-lookup"><span data-stu-id="16dcb-110">If the object does, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> is called on the object.</span></span>
  
- <span data-ttu-id="16dcb-111">若物件未實作 <xref:System.Runtime.Serialization.ISerializable>，且使用預設序列化原則，則會序列化所有未標記為 [NonSerialized](xref:System.NonSerializedAttribute) 的欄位。</span><span class="sxs-lookup"><span data-stu-id="16dcb-111">If the object does not implement <xref:System.Runtime.Serialization.ISerializable>, the default serialization policy is used, serializing all fields not marked as [NonSerialized](xref:System.NonSerializedAttribute).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="16dcb-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16dcb-112">See also</span></span>

- [<span data-ttu-id="16dcb-113">二進位序列化</span><span class="sxs-lookup"><span data-stu-id="16dcb-113">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="16dcb-114">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="16dcb-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
