---
title: ICorProfilerCallback3::ProfilerDetachSucceeded 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type:
- apiref
ms.openlocfilehash: b044c493649b73566a2e70db2e19977a6a7b877d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439455"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a>ICorProfilerCallback3::ProfilerDetachSucceeded 方法
通知分析工具 Common Language Runtime (CLR) 即將卸載分析工具 DLL。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a>傳回值  
 忽略此回呼傳回的值。  
  
## <a name="remarks"></a>備註  
 所有執行緒都結束分析工具的程式碼後，就會核發 `ProfilerDetachSucceeded` 回呼。 呼叫這個方法時，分析工具應該執行任何不適合其解構函式的最後一刻工作，例如通知其 UI 或記錄元件。 However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) or `IMetaData*` interfaces).  
  
 CLR 會在 Windows 應用程式事件記錄檔中建立項目，表示中斷連結作業成功。  
  
 分析工具從回呼傳回之後，CLR 釋放此分析工具物件並卸載分析工具 DLL。 因此，在分析工具從此回呼傳回之後，不可執行任何可能導致在分析工具 DLL 中執行的動作。 例如，它不可建立執行緒或註冊計時器回呼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [ICorProfilerInfo3 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
