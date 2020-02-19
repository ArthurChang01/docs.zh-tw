---
title: 日期和時間資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: bdcbaffe1be4933b89c7bf0d3a11e1bb871bc2bd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450294"
---
# <a name="date-and-time-data"></a><span data-ttu-id="60925-102">日期和時間資料</span><span class="sxs-lookup"><span data-stu-id="60925-102">Date and Time Data</span></span>
<span data-ttu-id="60925-103">SQL Server 2008 導入了處理日期和時間資訊的新資料型別。</span><span class="sxs-lookup"><span data-stu-id="60925-103">SQL Server 2008 introduces new data types for handling date and time information.</span></span> <span data-ttu-id="60925-104">這些新資料型別包括日期和時間的個別型別，以及具有較大範圍、精確度和時區感知的擴充資料型別。</span><span class="sxs-lookup"><span data-stu-id="60925-104">The new data types include separate types for date and time, and expanded data types with greater range, precision, and time-zone awareness.</span></span> <span data-ttu-id="60925-105">從 .NET Framework 3.5 版 Service Pack (SP) 1 開始，.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) 就會針對 SQL Server 2008 Database Engine 的所有新功能提供完整支援。</span><span class="sxs-lookup"><span data-stu-id="60925-105">Starting with the .NET Framework version 3.5 Service Pack (SP) 1, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides full support for all the new features of the SQL Server 2008 Database Engine.</span></span> <span data-ttu-id="60925-106">您必須安裝 .NET Framework 3.5 SP1 (或更新版本) 才能使用這些新功能搭配 SqlClient。</span><span class="sxs-lookup"><span data-stu-id="60925-106">You must install the .NET Framework 3.5 SP1 (or later) to use these new features with SqlClient.</span></span>  
  
 <span data-ttu-id="60925-107">SQL Server 2008 之前的 SQL Server 版本只有兩種可使用日期及時間值的資料型別：`datetime` 和 `smalldatetime`。</span><span class="sxs-lookup"><span data-stu-id="60925-107">Versions of SQL Server earlier than SQL Server 2008 only had two data types for working with date and time values: `datetime` and `smalldatetime`.</span></span> <span data-ttu-id="60925-108">這兩種資料類型都同時包含日期值和時間值，所以很難只使用日期或是時間值。</span><span class="sxs-lookup"><span data-stu-id="60925-108">Both of these data types contain both the date value and a time value, which makes it difficult to work with only date or only time values.</span></span> <span data-ttu-id="60925-109">此外，這些資料型別只支援發生在 1753 年英國西曆引進之後的日期。</span><span class="sxs-lookup"><span data-stu-id="60925-109">Also, these data types only support dates that occur after the introduction of the Gregorian calendar in England in 1753.</span></span> <span data-ttu-id="60925-110">另一項限制是這些較舊的資料型別並不具有時區感知的功能，所以不能使用源自多個時區的資料。</span><span class="sxs-lookup"><span data-stu-id="60925-110">Another limitation is that these older data types are not time-zone aware, which makes it difficult to work with data that originates from multiple time zones.</span></span>  
  
 <span data-ttu-id="60925-111">您可以在《SQL Server 線上叢書》中取得 SQL Server 資料型別的完整文件。</span><span class="sxs-lookup"><span data-stu-id="60925-111">Complete documentation for SQL Server data types is available in SQL Server Books Online.</span></span> <span data-ttu-id="60925-112">下表將列出日期和時間資料的版本特有入門級主題。</span><span class="sxs-lookup"><span data-stu-id="60925-112">The following table lists the version-specific entry-level topics for date and time data.</span></span>  
  
 <span data-ttu-id="60925-113">**SQL Server 文件**</span><span class="sxs-lookup"><span data-stu-id="60925-113">**SQL Server documentation**</span></span>  
  
1. <span data-ttu-id="60925-114">[使用日期和時間資料](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="60925-114">[Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span></span>  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a><span data-ttu-id="60925-115">SQL Server 2008 所導入的日期/時間資料型別</span><span class="sxs-lookup"><span data-stu-id="60925-115">Date/Time Data Types Introduced in SQL Server 2008</span></span>  
 <span data-ttu-id="60925-116">下表將描述新的日期和時間資料型別。</span><span class="sxs-lookup"><span data-stu-id="60925-116">The following table describes the new date and time data types.</span></span>  
  
|<span data-ttu-id="60925-117">SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="60925-117">SQL Server data type</span></span>|<span data-ttu-id="60925-118">描述</span><span class="sxs-lookup"><span data-stu-id="60925-118">Description</span></span>|  
|--------------------------|-----------------|  
|`date`|<span data-ttu-id="60925-119">`date` 資料類型的範圍從 01 年 1 月 1 日到 9999 年 12 月 31 日，精確度為 1 日。</span><span class="sxs-lookup"><span data-stu-id="60925-119">The `date` data type has a range of January 1, 01 through December 31, 9999 with an accuracy of 1 day.</span></span> <span data-ttu-id="60925-120">預設值為 1900 年 1 月 1 日。</span><span class="sxs-lookup"><span data-stu-id="60925-120">The default value is January 1, 1900.</span></span> <span data-ttu-id="60925-121">儲存體大小是 3 位元組。</span><span class="sxs-lookup"><span data-stu-id="60925-121">The storage size is 3 bytes.</span></span>|  
|`time`|<span data-ttu-id="60925-122">`time` 資料類型只會根據 24 小時制來儲存時間值。</span><span class="sxs-lookup"><span data-stu-id="60925-122">The `time` data type stores time values only, based on a 24-hour clock.</span></span> <span data-ttu-id="60925-123">`time` 資料型別的範圍從 00:00:00.0000000 到 23:59:59.9999999，精確度為 100 奈秒。</span><span class="sxs-lookup"><span data-stu-id="60925-123">The `time` data type has a range of 00:00:00.0000000 through 23:59:59.9999999 with an accuracy of 100 nanoseconds.</span></span> <span data-ttu-id="60925-124">預設值是 00:00:00.0000000 (午夜)。</span><span class="sxs-lookup"><span data-stu-id="60925-124">The default value is 00:00:00.0000000 (midnight).</span></span> <span data-ttu-id="60925-125">`time` 資料類型支援使用者定義的小數點後第二位的精確度，儲存大小則從 3 到 6 位元組不等，依指定的精確度而定。</span><span class="sxs-lookup"><span data-stu-id="60925-125">The `time` data type supports user-defined fractional second precision, and the storage size varies from 3 to 6 bytes, based on the precision specified.</span></span>|  
|`datetime2`|<span data-ttu-id="60925-126">`datetime2` 資料型別將 `date` 和 `time` 資料型別的範圍及精確度組合成單一的資料型別。</span><span class="sxs-lookup"><span data-stu-id="60925-126">The `datetime2` data type combines the range and precision of the `date` and `time` data types into a single data type.</span></span><br /><br /> <span data-ttu-id="60925-127">預設值及字串常值格式與 `date` 和 `time` 資料型別中定義的相同。</span><span class="sxs-lookup"><span data-stu-id="60925-127">The default values and string literal formats are the same as those defined in the `date` and `time` data types.</span></span>|  
|`datetimeoffset`|<span data-ttu-id="60925-128">`datetimeoffset` 資料類型具有 `datetime2` 的所有功能，且具有額外的時區位移。</span><span class="sxs-lookup"><span data-stu-id="60925-128">The `datetimeoffset` data type has all the features of `datetime2` with an additional time zone offset.</span></span> <span data-ttu-id="60925-129">時區位移會以 [+&#124;-] HH:MM 表示。</span><span class="sxs-lookup"><span data-stu-id="60925-129">The time zone offset is represented as [+&#124;-] HH:MM.</span></span> <span data-ttu-id="60925-130">HH 表示時區位移中的 2 位數時數，範圍介於 00 至 14 之間。</span><span class="sxs-lookup"><span data-stu-id="60925-130">HH is 2 digits ranging from 00 to 14 that represent the number of hours in the time zone offset.</span></span> <span data-ttu-id="60925-131">MM 是代表時區位移中額外分鐘數的 2 位數，範圍介於 00 至 59 之間。</span><span class="sxs-lookup"><span data-stu-id="60925-131">MM is 2 digits ranging from 00 to 59 that represent the number of additional minutes in the time zone offset.</span></span> <span data-ttu-id="60925-132">時間格式可支援到 100 奈秒。</span><span class="sxs-lookup"><span data-stu-id="60925-132">Time formats are supported to 100 nanoseconds.</span></span> <span data-ttu-id="60925-133">強制的 + 或 - 號則代表在取得當地時間時，是在 UTC (世界標準時間或格林威治標準時間) 中加入或減去時區位移數。</span><span class="sxs-lookup"><span data-stu-id="60925-133">The mandatory + or - sign indicates whether the time zone offset is added or subtracted from UTC (Universal Time Coordinate or Greenwich Mean Time) to obtain the local time.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="60925-134">如需使用 `Type System Version` 關鍵字的詳細資訊，請參閱 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="60925-134">For more information about using the `Type System Version` keyword, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
## <a name="date-format-and-date-order"></a><span data-ttu-id="60925-135">日期格式和日期順序</span><span class="sxs-lookup"><span data-stu-id="60925-135">Date Format and Date Order</span></span>  
 <span data-ttu-id="60925-136">SQL Server 剖析日期和時間值的方式不僅取決於型別系統版本和伺服器版本，而且也取決於伺服器的預設語言和格式設定。</span><span class="sxs-lookup"><span data-stu-id="60925-136">How SQL Server parses date and time values depends not only on the type system version and server version, but also on the server's default language and format settings.</span></span> <span data-ttu-id="60925-137">如果透過連接執行查詢，而連接是使用不同的語言與日期格式設定，那麼原先在另一種語言中日期格式有效的日期字串可能會變成無法辨識。</span><span class="sxs-lookup"><span data-stu-id="60925-137">A date string that works for the date formats of one language might be unrecognizable if the query is executed by a connection that uses a different language and date format setting.</span></span>  
  
 <span data-ttu-id="60925-138">Transact-SQL SET LANGUAGE 陳述式 (Statement) 會隱含地設定可決定日期部分順序的 DATEFORMAT。</span><span class="sxs-lookup"><span data-stu-id="60925-138">The Transact-SQL SET LANGUAGE statement implicitly sets the DATEFORMAT that determines the order of the date parts.</span></span> <span data-ttu-id="60925-139">您可以在連接時使用 SET DATEFORMAT Transact-SQL 陳述式，按照 MDY、DMY、YMD、YDM、MYD 或 DYM 順序排序日期部分，藉以讓日期值意義明確。</span><span class="sxs-lookup"><span data-stu-id="60925-139">You can use the SET DATEFORMAT Transact-SQL statement on a connection to disambiguate date values by ordering the date parts in MDY, DMY, YMD, YDM, MYD, or DYM order.</span></span>  
  
 <span data-ttu-id="60925-140">如果您沒有針對連接指定任何 DATEFORMAT，SQL Server 就會使用與連接相關聯的預設語言。</span><span class="sxs-lookup"><span data-stu-id="60925-140">If you do not specify any DATEFORMAT for the connection, SQL Server uses the default language associated with the connection.</span></span> <span data-ttu-id="60925-141">例如，日期字串 '01/02/03' 在語言設定為美式英文的伺服器上會解譯成 MDY (2003 年 1 月 2 日)，而在語言設定為英式英文的伺服器上則會解譯成 DMY (2003 年 2 月 1 日)。</span><span class="sxs-lookup"><span data-stu-id="60925-141">For example, a date string of '01/02/03' would be interpreted as MDY (January 2, 2003) on a server with a language setting of United States English, and as DMY (February 1, 2003) on a server with a language setting of British English.</span></span> <span data-ttu-id="60925-142">年份是使用 SQL Server 的截止年份規則決定的，而且此規則會定義指派世紀值的截止日期。</span><span class="sxs-lookup"><span data-stu-id="60925-142">The year is determined by using SQL Server's cutoff year rule, which defines the cutoff date for assigning the century value.</span></span> <span data-ttu-id="60925-143">如需詳細資訊，請參閱[兩位數年份的截止選項](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option)。</span><span class="sxs-lookup"><span data-stu-id="60925-143">For more information, see [two digit year cutoff Option](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60925-144">從字串格式轉換成 `date`、`time`、`datetime2` 或 `datetimeoffset` 時，不支援 YDM 日期格式。</span><span class="sxs-lookup"><span data-stu-id="60925-144">The YDM date format is not supported when converting from a string format to `date`, `time`, `datetime2`, or `datetimeoffset`.</span></span>  
  
 <span data-ttu-id="60925-145">如需 SQL Server 如何解讀日期和時間資料的詳細資訊，請參閱[使用日期和時間資料](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))。</span><span class="sxs-lookup"><span data-stu-id="60925-145">For more information about how SQL Server interprets date and time data, see [Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100)).</span></span>  
  
## <a name="datetime-data-types-and-parameters"></a><span data-ttu-id="60925-146">日期/時間資料型別和參數</span><span class="sxs-lookup"><span data-stu-id="60925-146">Date/Time Data Types and Parameters</span></span>  
 <span data-ttu-id="60925-147"><xref:System.Data.SqlDbType> 中已加入下列的列舉型別以支援新的日期及時間資料型別。</span><span class="sxs-lookup"><span data-stu-id="60925-147">The following enumerations have been added to <xref:System.Data.SqlDbType> to support the new date and time data types.</span></span>  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

<span data-ttu-id="60925-148">您可以使用上述其中一個 <xref:System.Data.SqlClient.SqlParameter> 列舉來指定 <xref:System.Data.SqlDbType> 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="60925-148">You can specify the data type of a <xref:System.Data.SqlClient.SqlParameter> by using one of the preceding <xref:System.Data.SqlDbType> enumerations.</span></span> 

> [!NOTE]
> <span data-ttu-id="60925-149">您無法將 `SqlParameter` 的 `DbType` 屬性設定為 [`SqlDbType.Date`]。</span><span class="sxs-lookup"><span data-stu-id="60925-149">You cannot set the `DbType` property of a `SqlParameter` to `SqlDbType.Date`.</span></span>

 <span data-ttu-id="60925-150">您也可以藉由將 <xref:System.Data.SqlClient.SqlParameter> 物件的 <xref:System.Data.SqlClient.SqlParameter.DbType%2A> 屬性設定為特定的 `SqlParameter` 列舉值，以一般的方法指定 <xref:System.Data.DbType> 的類型。</span><span class="sxs-lookup"><span data-stu-id="60925-150">You can also specify the type of a <xref:System.Data.SqlClient.SqlParameter> generically by setting the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> property of a `SqlParameter` object to a particular <xref:System.Data.DbType> enumeration value.</span></span> <span data-ttu-id="60925-151"><xref:System.Data.DbType> 中新增了以下列舉值，以支援 `datetime2` 和 `datetimeoffset` 資料類型：</span><span class="sxs-lookup"><span data-stu-id="60925-151">The following enumeration values have been added to <xref:System.Data.DbType> to support the `datetime2` and `datetimeoffset` data types:</span></span>  
  
- <span data-ttu-id="60925-152">DbType.DateTime2</span><span class="sxs-lookup"><span data-stu-id="60925-152">DbType.DateTime2</span></span>  
  
- <span data-ttu-id="60925-153">DbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="60925-153">DbType.DateTimeOffset</span></span>  
  
 <span data-ttu-id="60925-154">這些新的列舉型別補充了存在舊版 .NET Framework 中的 `Date`、`Time` 和 `DateTime` 列舉型別。</span><span class="sxs-lookup"><span data-stu-id="60925-154">These new enumerations supplement the `Date`, `Time`, and `DateTime` enumerations, which existed in earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="60925-155">您可以從參數物件之值的 .NET Framework 型別，或從參數物件的 `DbType` 推斷出參數物件的 .NET Framework 資料提供者型別。</span><span class="sxs-lookup"><span data-stu-id="60925-155">The .NET Framework data provider type of a parameter object is inferred from the .NET Framework type of the value of the parameter object, or from the `DbType` of the parameter object.</span></span> <span data-ttu-id="60925-156">尚未引進任何新增的 <xref:System.Data.SqlTypes> 來支援新的日期及時間資料型別。</span><span class="sxs-lookup"><span data-stu-id="60925-156">No new <xref:System.Data.SqlTypes> data types have been introduced to support the new date and time data types.</span></span> <span data-ttu-id="60925-157">下表說明 SQL Server 2008 日期和時間資料型別以及 CLR 資料型別之間的對應。</span><span class="sxs-lookup"><span data-stu-id="60925-157">The following table describes the mappings between the SQL Server 2008 date and time data types and the CLR data types.</span></span>  
  
|<span data-ttu-id="60925-158">SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="60925-158">SQL Server data type</span></span>|<span data-ttu-id="60925-159">.NET Framework 類型</span><span class="sxs-lookup"><span data-stu-id="60925-159">.NET Framework type</span></span>|<span data-ttu-id="60925-160">System.Data.SqlDbType</span><span class="sxs-lookup"><span data-stu-id="60925-160">System.Data.SqlDbType</span></span>|<span data-ttu-id="60925-161">System.Data.DbType</span><span class="sxs-lookup"><span data-stu-id="60925-161">System.Data.DbType</span></span>|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|<span data-ttu-id="60925-162">date</span><span class="sxs-lookup"><span data-stu-id="60925-162">date</span></span>|<span data-ttu-id="60925-163">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="60925-163">System.DateTime</span></span>|<span data-ttu-id="60925-164">Date</span><span class="sxs-lookup"><span data-stu-id="60925-164">Date</span></span>|<span data-ttu-id="60925-165">Date</span><span class="sxs-lookup"><span data-stu-id="60925-165">Date</span></span>|  
|<span data-ttu-id="60925-166">time</span><span class="sxs-lookup"><span data-stu-id="60925-166">time</span></span>|<span data-ttu-id="60925-167">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="60925-167">System.TimeSpan</span></span>|<span data-ttu-id="60925-168">Time</span><span class="sxs-lookup"><span data-stu-id="60925-168">Time</span></span>|<span data-ttu-id="60925-169">Time</span><span class="sxs-lookup"><span data-stu-id="60925-169">Time</span></span>|  
|<span data-ttu-id="60925-170">datetime2</span><span class="sxs-lookup"><span data-stu-id="60925-170">datetime2</span></span>|<span data-ttu-id="60925-171">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="60925-171">System.DateTime</span></span>|<span data-ttu-id="60925-172">DateTime2</span><span class="sxs-lookup"><span data-stu-id="60925-172">DateTime2</span></span>|<span data-ttu-id="60925-173">DateTime2</span><span class="sxs-lookup"><span data-stu-id="60925-173">DateTime2</span></span>|  
|<span data-ttu-id="60925-174">datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="60925-174">datetimeoffset</span></span>|<span data-ttu-id="60925-175">System.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="60925-175">System.DateTimeOffset</span></span>|<span data-ttu-id="60925-176">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="60925-176">DateTimeOffset</span></span>|<span data-ttu-id="60925-177">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="60925-177">DateTimeOffset</span></span>|  
|<span data-ttu-id="60925-178">Datetime</span><span class="sxs-lookup"><span data-stu-id="60925-178">datetime</span></span>|<span data-ttu-id="60925-179">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="60925-179">System.DateTime</span></span>|<span data-ttu-id="60925-180">Datetime</span><span class="sxs-lookup"><span data-stu-id="60925-180">DateTime</span></span>|<span data-ttu-id="60925-181">Datetime</span><span class="sxs-lookup"><span data-stu-id="60925-181">DateTime</span></span>|  
|<span data-ttu-id="60925-182">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="60925-182">smalldatetime</span></span>|<span data-ttu-id="60925-183">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="60925-183">System.DateTime</span></span>|<span data-ttu-id="60925-184">Datetime</span><span class="sxs-lookup"><span data-stu-id="60925-184">DateTime</span></span>|<span data-ttu-id="60925-185">Datetime</span><span class="sxs-lookup"><span data-stu-id="60925-185">DateTime</span></span>|  
  
### <a name="sqlparameter-properties"></a><span data-ttu-id="60925-186">SqlParameter 屬性</span><span class="sxs-lookup"><span data-stu-id="60925-186">SqlParameter Properties</span></span>  
 <span data-ttu-id="60925-187">下表將說明與日期和時間資料型別相關的 `SqlParameter` 屬性。</span><span class="sxs-lookup"><span data-stu-id="60925-187">The following table describes `SqlParameter` properties that are relevant to date and time data types.</span></span>  
  
|<span data-ttu-id="60925-188">屬性</span><span class="sxs-lookup"><span data-stu-id="60925-188">Property</span></span>|<span data-ttu-id="60925-189">描述</span><span class="sxs-lookup"><span data-stu-id="60925-189">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|<span data-ttu-id="60925-190">取得或設定值是否可為 Null。</span><span class="sxs-lookup"><span data-stu-id="60925-190">Gets or sets whether a value is nullable.</span></span> <span data-ttu-id="60925-191">將 Null 參數值傳送至伺服器時，必須指定 <xref:System.DBNull>，而不是 `null` (在 Visual Basic 中為 `Nothing`)。</span><span class="sxs-lookup"><span data-stu-id="60925-191">When you send a null parameter value to the server, you must specify <xref:System.DBNull>, rather than `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="60925-192">如需資料庫 null 值的詳細資訊，請參閱 [Handling Null Values](handling-null-values.md)。</span><span class="sxs-lookup"><span data-stu-id="60925-192">For more information about database nulls, see [Handling Null Values](handling-null-values.md).</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|<span data-ttu-id="60925-193">取得或設定用來表示值的最大位數。</span><span class="sxs-lookup"><span data-stu-id="60925-193">Gets or sets the maximum number of digits used to represent the value.</span></span> <span data-ttu-id="60925-194">若為日期和時間資料型別，則會忽略這項設定。</span><span class="sxs-lookup"><span data-stu-id="60925-194">This setting is ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|<span data-ttu-id="60925-195">取得或設定針對 `Time`、`DateTime2` 和 `DateTimeOffset` 解析之值時間部分的小數點位數。</span><span class="sxs-lookup"><span data-stu-id="60925-195">Gets or sets the number of decimal places to which the time portion of the value is resolved for `Time`, `DateTime2`,and `DateTimeOffset`.</span></span> <span data-ttu-id="60925-196">預設值為 0，表示從此值推斷實際的小數點位數並傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="60925-196">The default value is 0, which means that the actual scale is inferred from the value and sent to the server.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="60925-197">若為日期和時間資料型別，則會忽略。</span><span class="sxs-lookup"><span data-stu-id="60925-197">Ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="60925-198">取得或設定參數值。</span><span class="sxs-lookup"><span data-stu-id="60925-198">Gets or sets the parameter value.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="60925-199">取得或設定參數值。</span><span class="sxs-lookup"><span data-stu-id="60925-199">Gets or sets the parameter value.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="60925-200">小於零或是大於或等於 24 小時的時間值將會擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="60925-200">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
### <a name="creating-parameters"></a><span data-ttu-id="60925-201">建立參數</span><span class="sxs-lookup"><span data-stu-id="60925-201">Creating Parameters</span></span>  
 <span data-ttu-id="60925-202">您可以使用 <xref:System.Data.SqlClient.SqlParameter> 物件的建構函式 (Constructor)，或將它加入至 <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> 集合 (透過呼叫 `Add` 的 <xref:System.Data.SqlClient.SqlParameterCollection> 方法)，藉以建立此物件。</span><span class="sxs-lookup"><span data-stu-id="60925-202">You can create a <xref:System.Data.SqlClient.SqlParameter> object by using its constructor, or by adding it to a <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection by calling the `Add` method of the <xref:System.Data.SqlClient.SqlParameterCollection>.</span></span> <span data-ttu-id="60925-203">`Add` 方法會將建構函式引數或現有的參數物件當做輸入。</span><span class="sxs-lookup"><span data-stu-id="60925-203">The `Add` method will take as input either constructor arguments or an existing parameter object.</span></span>  
  
 <span data-ttu-id="60925-204">本主題的下列章節會提供如何指定 date 和 time 參數的範例。</span><span class="sxs-lookup"><span data-stu-id="60925-204">The next sections in this topic provide examples of how to specify date and time parameters.</span></span> <span data-ttu-id="60925-205">如需使用參數的其他範例，請參閱設定[參數和參數資料類型](../configuring-parameters-and-parameter-data-types.md)和[DataAdapter 參數](../dataadapter-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="60925-205">For additional examples of working with parameters, see [Configuring Parameters and Parameter Data Types](../configuring-parameters-and-parameter-data-types.md) and [DataAdapter Parameters](../dataadapter-parameters.md).</span></span>  
  
### <a name="date-example"></a><span data-ttu-id="60925-206">Date 範例</span><span class="sxs-lookup"><span data-stu-id="60925-206">Date Example</span></span>  
 <span data-ttu-id="60925-207">下列程式碼片段將示範如何指定 `date` 參數。</span><span class="sxs-lookup"><span data-stu-id="60925-207">The following code fragment demonstrates how to specify a `date` parameter.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Date";  
parameter.SqlDbType = SqlDbType.Date;  
parameter.Value = "2007/12/1";  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Date"  
parameter.SqlDbType = SqlDbType.Date  
parameter.Value = "2007/12/1"  
```  
  
### <a name="time-example"></a><span data-ttu-id="60925-208">Time 範例</span><span class="sxs-lookup"><span data-stu-id="60925-208">Time Example</span></span>  
 <span data-ttu-id="60925-209">下列程式碼片段將示範如何指定 `time` 參數。</span><span class="sxs-lookup"><span data-stu-id="60925-209">The following code fragment demonstrates how to specify a `time` parameter.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@time";  
parameter.SqlDbType = SqlDbType.Time;  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Time"  
parameter.SqlDbType = SqlDbType.Time  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
### <a name="datetime2-example"></a><span data-ttu-id="60925-210">Datetime2 範例</span><span class="sxs-lookup"><span data-stu-id="60925-210">Datetime2 Example</span></span>  
 <span data-ttu-id="60925-211">下列程式碼片段將示範如何指定同時含有日期和時間部分的 `datetime2` 參數。</span><span class="sxs-lookup"><span data-stu-id="60925-211">The following code fragment demonstrates how to specify a `datetime2` parameter with both the date and time parts.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Datetime2";  
parameter.SqlDbType = SqlDbType.DateTime2;  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Datetime2"  
parameter.SqlDbType = SqlDbType.DateTime2  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
### <a name="datetimeoffset-example"></a><span data-ttu-id="60925-212">DateTimeOffSet 範例</span><span class="sxs-lookup"><span data-stu-id="60925-212">DateTimeOffSet Example</span></span>  
 <span data-ttu-id="60925-213">下列程式碼片段將示範如何指定含有日期、時間和時區位移 0 的 `DateTimeOffSet` 參數。</span><span class="sxs-lookup"><span data-stu-id="60925-213">The following code fragment demonstrates how to specify a `DateTimeOffSet` parameter with a date, a time, and a time zone offset of 0.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@DateTimeOffSet";  
parameter.SqlDbType = SqlDbType.DateTimeOffSet;  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@DateTimeOffSet"  
parameter.SqlDbType = SqlDbType.DateTimeOffSet  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
### <a name="addwithvalue"></a><span data-ttu-id="60925-214">AddWithValue</span><span class="sxs-lookup"><span data-stu-id="60925-214">AddWithValue</span></span>  
 <span data-ttu-id="60925-215">您也可以使用 `AddWithValue` 的 <xref:System.Data.SqlClient.SqlCommand> 方法來提供參數，如下列程式碼片段所示。</span><span class="sxs-lookup"><span data-stu-id="60925-215">You can also supply parameters by using the `AddWithValue` method of a <xref:System.Data.SqlClient.SqlCommand>, as shown in the following code fragment.</span></span> <span data-ttu-id="60925-216">不過，`AddWithValue` 方法不允許您指定參數的 <xref:System.Data.SqlClient.SqlParameter.DbType%2A> 或 <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A>。</span><span class="sxs-lookup"><span data-stu-id="60925-216">However, the `AddWithValue` method does not allow you to specify the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> or <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> for the parameter.</span></span>  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 <span data-ttu-id="60925-217">`@date` 參數可對應至伺服器上的 `date`、`datetime` 或 `datetime2` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="60925-217">The `@date` parameter could map to a `date`, `datetime`, or `datetime2` data type on the server.</span></span> <span data-ttu-id="60925-218">使用新的 `datetime` 資料型別時，您必須明確將此參數的 <xref:System.Data.SqlDbType> 屬性設定為執行個體 (Instance) 的資料型別。</span><span class="sxs-lookup"><span data-stu-id="60925-218">When working with the new `datetime` data types, you must explicitly set the parameter's <xref:System.Data.SqlDbType> property to the data type of the instance.</span></span> <span data-ttu-id="60925-219">使用 <xref:System.Data.SqlDbType.Variant> 或隱含地提供參數值可能會導致與 `datetime` 和 `smalldatetime` 資料型別的回溯相容性 (Backward Compatibility) 問題。</span><span class="sxs-lookup"><span data-stu-id="60925-219">Using <xref:System.Data.SqlDbType.Variant> or implicitly supplying parameter values can cause problems with backward compatibility with the `datetime` and `smalldatetime` data types.</span></span>  
  
 <span data-ttu-id="60925-220">下表將顯示從哪些 CLR 型別推斷哪些 `SqlDbTypes`：</span><span class="sxs-lookup"><span data-stu-id="60925-220">The following table shows which `SqlDbTypes` are inferred from which CLR types:</span></span>  
  
|<span data-ttu-id="60925-221">CLR 類型</span><span class="sxs-lookup"><span data-stu-id="60925-221">CLR type</span></span>|<span data-ttu-id="60925-222">推斷的 SqlDbType</span><span class="sxs-lookup"><span data-stu-id="60925-222">Inferred SqlDbType</span></span>|  
|--------------|------------------------|  
|<span data-ttu-id="60925-223">Datetime</span><span class="sxs-lookup"><span data-stu-id="60925-223">DateTime</span></span>|<span data-ttu-id="60925-224">SqlDbType.DateTime</span><span class="sxs-lookup"><span data-stu-id="60925-224">SqlDbType.DateTime</span></span>|  
|<span data-ttu-id="60925-225">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="60925-225">TimeSpan</span></span>|<span data-ttu-id="60925-226">SqlDbType.Time</span><span class="sxs-lookup"><span data-stu-id="60925-226">SqlDbType.Time</span></span>|  
|<span data-ttu-id="60925-227">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="60925-227">DateTimeOffset</span></span>|<span data-ttu-id="60925-228">SqlDbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="60925-228">SqlDbType.DateTimeOffset</span></span>|  
  
## <a name="retrieving-date-and-time-data"></a><span data-ttu-id="60925-229">擷取日期和時間資料</span><span class="sxs-lookup"><span data-stu-id="60925-229">Retrieving Date and Time Data</span></span>  
 <span data-ttu-id="60925-230">下表說明用來擷取 SQL Server 2008 日期和時間值的方法。</span><span class="sxs-lookup"><span data-stu-id="60925-230">The following table describes methods that are used to retrieve SQL Server 2008 date and time values.</span></span>  
  
|<span data-ttu-id="60925-231">SqlClient 方法</span><span class="sxs-lookup"><span data-stu-id="60925-231">SqlClient method</span></span>|<span data-ttu-id="60925-232">描述</span><span class="sxs-lookup"><span data-stu-id="60925-232">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|<span data-ttu-id="60925-233">擷取指定的資料行值作為 <xref:System.DateTime> 結構。</span><span class="sxs-lookup"><span data-stu-id="60925-233">Retrieves the specified column value as a <xref:System.DateTime> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|<span data-ttu-id="60925-234">擷取指定的資料行值作為 <xref:System.DateTimeOffset> 結構。</span><span class="sxs-lookup"><span data-stu-id="60925-234">Retrieves the specified column value as a <xref:System.DateTimeOffset> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|<span data-ttu-id="60925-235">傳回的型別是欄位基礎提供者特定的型別。</span><span class="sxs-lookup"><span data-stu-id="60925-235">Returns the type that is the underlying provider-specific type for the field.</span></span> <span data-ttu-id="60925-236">針對新的日期和時間型別，傳回與 `GetFieldType` 相同的型別。</span><span class="sxs-lookup"><span data-stu-id="60925-236">Returns the same types as `GetFieldType` for new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|<span data-ttu-id="60925-237">擷取指定資料行的值。</span><span class="sxs-lookup"><span data-stu-id="60925-237">Retrieves the value of the specified column.</span></span> <span data-ttu-id="60925-238">針對新的日期和時間型別，傳回與 `GetValue` 相同的型別。</span><span class="sxs-lookup"><span data-stu-id="60925-238">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|<span data-ttu-id="60925-239">擷取指定陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="60925-239">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<span data-ttu-id="60925-240">以 <xref:System.Data.SqlTypes.SqlString> 擷取資料行值。</span><span class="sxs-lookup"><span data-stu-id="60925-240">Retrieves the column value as a <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="60925-241">如果資料無法以 <xref:System.InvalidCastException> 表示，就會發生 `SqlString`。</span><span class="sxs-lookup"><span data-stu-id="60925-241">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a `SqlString`.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|<span data-ttu-id="60925-242">擷取資料行的資料，做為其預設 `SqlDbType`。</span><span class="sxs-lookup"><span data-stu-id="60925-242">Retrieves column data as its default `SqlDbType`.</span></span> <span data-ttu-id="60925-243">針對新的日期和時間型別，傳回與 `GetValue` 相同的型別。</span><span class="sxs-lookup"><span data-stu-id="60925-243">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|<span data-ttu-id="60925-244">擷取指定陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="60925-244">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|<span data-ttu-id="60925-245">如果 Type System Version 是設為 SQL Server 2005，則擷取資料行的值作為字串。</span><span class="sxs-lookup"><span data-stu-id="60925-245">Retrieves the column value as a string if the Type System Version is set to SQL Server 2005.</span></span> <span data-ttu-id="60925-246">如果資料無法以字串表示，就會發生 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="60925-246">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a string.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|<span data-ttu-id="60925-247">擷取指定的資料行值作為 <xref:System.TimeSpan> 結構。</span><span class="sxs-lookup"><span data-stu-id="60925-247">Retrieves the specified column value as a <xref:System.TimeSpan> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|<span data-ttu-id="60925-248">擷取指定資料行的值做為其基礎的 CLR 型別。</span><span class="sxs-lookup"><span data-stu-id="60925-248">Retrieves the specified column value as its underlying CLR type.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|<span data-ttu-id="60925-249">擷取陣列中的資料行值。</span><span class="sxs-lookup"><span data-stu-id="60925-249">Retrieves column values in an array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|<span data-ttu-id="60925-250">傳回說明結果集中繼資料的 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="60925-250">Returns a <xref:System.Data.DataTable> that describes the metadata of the result set.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="60925-251">新的日期和時間 `SqlDbTypes` 不支援 SQL Server 中同處理序 (In-Process) 執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="60925-251">The new date and time `SqlDbTypes` are not supported for code that is executing in-process in SQL Server.</span></span> <span data-ttu-id="60925-252">如果其中一個型別傳遞至伺服器，就會引發例外狀況 (Exception)。</span><span class="sxs-lookup"><span data-stu-id="60925-252">An exception will be raised if one of these types is passed to the server.</span></span>  
  
## <a name="specifying-date-and-time-values-as-literals"></a><span data-ttu-id="60925-253">將日期和時間值指定為常值</span><span class="sxs-lookup"><span data-stu-id="60925-253">Specifying Date and Time Values as Literals</span></span>  
 <span data-ttu-id="60925-254">您可以使用各種不同的常值字串格式來指定日期和時間資料型別，然後 SQL Server 就會在執行階段評估這些格式，並將它們轉換成內部日期/時間結構。</span><span class="sxs-lookup"><span data-stu-id="60925-254">You can specify date and time data types by using a variety of different literal string formats, which SQL Server then evaluates at run time, converting them to internal date/time structures.</span></span> <span data-ttu-id="60925-255">SQL Server 可辨識以單引號 (') 括住的日期和時間資料。</span><span class="sxs-lookup"><span data-stu-id="60925-255">SQL Server recognizes date and time data that is enclosed in single quotation marks (').</span></span> <span data-ttu-id="60925-256">下列範例將示範一些格式：</span><span class="sxs-lookup"><span data-stu-id="60925-256">The following examples demonstrate some formats:</span></span>  
  
- <span data-ttu-id="60925-257">字母日期格式，例如 `'October 15, 2006'`。</span><span class="sxs-lookup"><span data-stu-id="60925-257">Alphabetic date formats, such as `'October 15, 2006'`.</span></span>  
  
- <span data-ttu-id="60925-258">數字日期格式，例如 `'10/15/2006'`。</span><span class="sxs-lookup"><span data-stu-id="60925-258">Numeric date formats, such as `'10/15/2006'`.</span></span>  
  
- <span data-ttu-id="60925-259">未分隔的字串格式，例如 `'20061015'`。如果您正在使用 ISO 標準日期格式，它就會解譯成 2006 年 10 月 15 日。</span><span class="sxs-lookup"><span data-stu-id="60925-259">Unseparated string formats, such as `'20061015'`, which would be interpreted as October 15, 2006 if you are using the ISO standard date format.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60925-260">您可以在《SQL Server 線上叢書》中找到所有常值字串格式以及日期和時間資料型別之其他功能的完整文件。</span><span class="sxs-lookup"><span data-stu-id="60925-260">You can find complete documentation for all of the literal string formats and other features of the date and time data types in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="60925-261">小於零或是大於或等於 24 小時的時間值將會擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="60925-261">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="60925-262">SQL Server 線上叢書中的資源</span><span class="sxs-lookup"><span data-stu-id="60925-262">Resources in SQL Server Books Online</span></span>  
 <span data-ttu-id="60925-263">如需在 SQL Server 中使用日期和時間值的詳細資訊，請參閱 SQL Server 線上叢書中的下列資源。</span><span class="sxs-lookup"><span data-stu-id="60925-263">For more information about working with date and time values in SQL Server, see the following resources in SQL Server Books Online.</span></span>  
  
|<span data-ttu-id="60925-264">主題</span><span class="sxs-lookup"><span data-stu-id="60925-264">Topic</span></span>|<span data-ttu-id="60925-265">描述</span><span class="sxs-lookup"><span data-stu-id="60925-265">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="60925-266">日期與時間資料類型及函式 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="60925-266">Date and Time Data Types and Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|<span data-ttu-id="60925-267">提供所有 Transact-SQL 日期和間資料類型與函式的概觀。</span><span class="sxs-lookup"><span data-stu-id="60925-267">Provides an overview of all Transact-SQL date and time data types and functions.</span></span>|  
|<span data-ttu-id="60925-268">[使用日期和時間資料](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="60925-268">[Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span></span>|<span data-ttu-id="60925-269">提供日期和時間資料類型與函式的詳細資訊，以及使用範例。</span><span class="sxs-lookup"><span data-stu-id="60925-269">Provides information about the date and time data types and functions, and examples of using them.</span></span>|  
|[<span data-ttu-id="60925-270">資料類型 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="60925-270">Data Types (Transact-SQL)</span></span>](/sql/t-sql/data-types/data-types-transact-sql)|<span data-ttu-id="60925-271">描述 SQL Server 中的系統資料類型。</span><span class="sxs-lookup"><span data-stu-id="60925-271">Describes system data types in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60925-272">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60925-272">See also</span></span>

- [<span data-ttu-id="60925-273">SQL Server 資料類型對應</span><span class="sxs-lookup"><span data-stu-id="60925-273">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="60925-274">設定參數和參數資料類型</span><span class="sxs-lookup"><span data-stu-id="60925-274">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="60925-275">SQL Server 資料類型和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="60925-275">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="60925-276">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="60925-276">ADO.NET Overview</span></span>](../ado-net-overview.md)
