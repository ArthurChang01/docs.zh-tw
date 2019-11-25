---
title: Members
description: 瞭解程式設計語言中的F#物件成員。
ms.date: 05/16/2016
ms.openlocfilehash: 2e85d014cd1e9b7997638cb210fed5705c217719
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425075"
---
# <a name="members"></a><span data-ttu-id="7c14e-103">Members</span><span class="sxs-lookup"><span data-stu-id="7c14e-103">Members</span></span>

<span data-ttu-id="7c14e-104">本節描述 F# 物件類型的成員。</span><span class="sxs-lookup"><span data-stu-id="7c14e-104">This section describes members of F# object types.</span></span>

## <a name="remarks"></a><span data-ttu-id="7c14e-105">備註</span><span class="sxs-lookup"><span data-stu-id="7c14e-105">Remarks</span></span>

<span data-ttu-id="7c14e-106">「成員」是作為類型定義的一部分且以 `member` 關鍵字宣告的功能。</span><span class="sxs-lookup"><span data-stu-id="7c14e-106">*Members* are features that are part of a type definition and are declared with the `member` keyword.</span></span> <span data-ttu-id="7c14e-107">F# 物件類型 (例如記錄、類別、差別聯集、介面和結構) 支援成員。</span><span class="sxs-lookup"><span data-stu-id="7c14e-107">F# object types such as records, classes, discriminated unions, interfaces, and structures support members.</span></span> <span data-ttu-id="7c14e-108">如需詳細資訊，請參閱[記錄](../records.md)、[類別](../classes.md)、[差別聯集](../discriminated-Unions.md)、[介面](../interfaces.md)和[結構](../structures.md)。</span><span class="sxs-lookup"><span data-stu-id="7c14e-108">For more information, see [Records](../records.md), [Classes](../classes.md), [Discriminated Unions](../discriminated-Unions.md), [Interfaces](../interfaces.md), and [Structures](../structures.md).</span></span>

<span data-ttu-id="7c14e-109">成員一般構成類型的公用介面，因此除非另外指定，否則成員為公用。</span><span class="sxs-lookup"><span data-stu-id="7c14e-109">Members typically make up the public interface for a type, which is why they are public unless otherwise specified.</span></span> <span data-ttu-id="7c14e-110">成員也可以宣告為私用或內用。</span><span class="sxs-lookup"><span data-stu-id="7c14e-110">Members can also be declared private or internal.</span></span> <span data-ttu-id="7c14e-111">如需詳細資訊，請參閱[存取控制](../access-Control.md)。</span><span class="sxs-lookup"><span data-stu-id="7c14e-111">For more information, see [Access Control](../access-Control.md).</span></span> <span data-ttu-id="7c14e-112">類型的簽章也可以用來公開或不公開類型的特定成員。</span><span class="sxs-lookup"><span data-stu-id="7c14e-112">Signatures for types can also be used to expose or not expose certain members of a type.</span></span> <span data-ttu-id="7c14e-113">如需詳細資訊，請參閱[簽章](../signature-files.md)。</span><span class="sxs-lookup"><span data-stu-id="7c14e-113">For more information, see [Signatures](../signature-files.md).</span></span>

<span data-ttu-id="7c14e-114">只與類別搭配使用的私用欄位和 `do` 繫結，並不是真正的成員，因為它們永遠不是類型之公用介面的一部分，也不是以 `member` 關鍵字宣告，但本節中也會加以描述。</span><span class="sxs-lookup"><span data-stu-id="7c14e-114">Private fields and `do` bindings, which are used only with classes, are not true members, because they are never part of the public interface of a type and are not declared with the `member` keyword, but they are described in this section also.</span></span>

## <a name="related-topics"></a><span data-ttu-id="7c14e-115">相關主題</span><span class="sxs-lookup"><span data-stu-id="7c14e-115">Related Topics</span></span>

|<span data-ttu-id="7c14e-116">主題</span><span class="sxs-lookup"><span data-stu-id="7c14e-116">Topic</span></span>|<span data-ttu-id="7c14e-117">描述</span><span class="sxs-lookup"><span data-stu-id="7c14e-117">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="7c14e-118">類別中的 `let` 繫結</span><span class="sxs-lookup"><span data-stu-id="7c14e-118">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)|<span data-ttu-id="7c14e-119">描述類別中私用欄位和函式的定義。</span><span class="sxs-lookup"><span data-stu-id="7c14e-119">Describes the definition of private fields and functions in classes.</span></span>|
|[<span data-ttu-id="7c14e-120">類別中的 `do` 繫結</span><span class="sxs-lookup"><span data-stu-id="7c14e-120">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)|<span data-ttu-id="7c14e-121">描述物件初始設定程式碼的規格。</span><span class="sxs-lookup"><span data-stu-id="7c14e-121">Describes the specification of object initialization code.</span></span>|
|[<span data-ttu-id="7c14e-122">內容</span><span class="sxs-lookup"><span data-stu-id="7c14e-122">Properties</span></span>](properties.md)|<span data-ttu-id="7c14e-123">描述類別和其他類型中的屬性成員。</span><span class="sxs-lookup"><span data-stu-id="7c14e-123">Describes property members in classes and other types.</span></span>|
|[<span data-ttu-id="7c14e-124">索引屬性</span><span class="sxs-lookup"><span data-stu-id="7c14e-124">Indexed Properties</span></span>](indexed-properties.md)|<span data-ttu-id="7c14e-125">描述類別和其他類型中的類似陣列屬性。</span><span class="sxs-lookup"><span data-stu-id="7c14e-125">Describes array-like properties in classes and other types.</span></span>|
|[<span data-ttu-id="7c14e-126">方法</span><span class="sxs-lookup"><span data-stu-id="7c14e-126">Methods</span></span>](methods.md)|<span data-ttu-id="7c14e-127">描述作為類型成員的函式。</span><span class="sxs-lookup"><span data-stu-id="7c14e-127">Describes functions that are members of a type.</span></span>|
|[<span data-ttu-id="7c14e-128">建構函式</span><span class="sxs-lookup"><span data-stu-id="7c14e-128">Constructors</span></span>](constructors.md)|<span data-ttu-id="7c14e-129">描述初始化型別物件的特殊函式。</span><span class="sxs-lookup"><span data-stu-id="7c14e-129">Describes special functions that initialize objects of a type.</span></span>|
|[<span data-ttu-id="7c14e-130">運算子多載</span><span class="sxs-lookup"><span data-stu-id="7c14e-130">Operator Overloading</span></span>](../operator-overloading.md)|<span data-ttu-id="7c14e-131">描述型別之自訂運算子的定義。</span><span class="sxs-lookup"><span data-stu-id="7c14e-131">Describes the definition of customized operators for types.</span></span>|
|[<span data-ttu-id="7c14e-132">事件</span><span class="sxs-lookup"><span data-stu-id="7c14e-132">Events</span></span>](events.md)|<span data-ttu-id="7c14e-133">描述 F# 中的事件定義和事件處理支援。</span><span class="sxs-lookup"><span data-stu-id="7c14e-133">Describes the definition of events and event handling support in F#.</span></span>|
|[<span data-ttu-id="7c14e-134">明確欄位：`val` 關鍵字</span><span class="sxs-lookup"><span data-stu-id="7c14e-134">Explicit Fields: The `val` Keyword</span></span>](explicit-fields-the-val-keyword.md)|<span data-ttu-id="7c14e-135">描述類型中未初始化欄位的定義。</span><span class="sxs-lookup"><span data-stu-id="7c14e-135">Describes the definition of uninitialized fields in a type.</span></span>|
