---
description: ExitCode プロパティ (SqlService クラス)
title: ExitCode プロパティ (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ExitCode Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ExitCode property
ms.assetid: e6b8bff2-946f-4abe-bd50-1f7bb11fdddf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ab792d72f904511bb17dda140132e86350255fa2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88446124"
---
# <a name="exitcode-property-sqlservice-class"></a>ExitCode プロパティ (SqlService クラス)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  サービスの開始時および停止時に検出される問題を定義した [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 エラー コードを取得または設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.ExitCode [= value]  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 サービスを表す [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 終了コードを指定する **uint32** 値。  
  
## <a name="remarks"></a>解説  
 このプロパティは、エラーがこのクラスによって表されているサービスに特有な場合には、ERROR_SERVICE_SPECIFIC_ERROR (1066) に設定されます。 サービスは、実行時にこの値を NO_ERROR に設定し、通常終了時にも再度設定します。  
  
## <a name="see-also"></a>参照  
 [サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
