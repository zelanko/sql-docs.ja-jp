---
title: SqlServiceType プロパティ (Sqlservicetype)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SqlServiceType Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SqlServiceType property
ms.assetid: dbff2968-3011-41d6-a141-52d814af0213
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: db0a9b0d2461e392f981ba3699a9efd3c1f3f8f3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73660876"
---
# <a name="sqlservicetype-property-sqlservice-class"></a>SqlServiceType プロパティ (SqlService クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  マネージド サービスの種類を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SqlServiceType [= value]  
```  
  
## <a name="parts"></a>要素  
 *素材*  
 サービスを表す [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サービスの[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]種類を指定する uint32 値。  
  
## <a name="remarks"></a>解説  
 戻り値は次のいずれかです。  
  
|種類|定義|  
|----------|----------------|  
|*1*|MSSQLSERVER は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスです。|  
|*2*|SQLSERVERAGENT は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント サービスです。|  
|*番*|MSFTESQL は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フルテキスト検索エンジン サービスです。|  
|*4*|MsDtsServer は [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] サービスです。|  
|*5/5*|MSSQLServerOLAPService は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サービスです。|  
|*6*|ReportServer は [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] サービスです。|  
|*7*|SQLBrowser は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser サービスです。|  
|*8*|Nsservice.exe は[!INCLUDE[ssNoVersion](../../../includes/ssns-md.md)] Notification service です。|  
|*9*|MSSQLFDLauncher は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]フルテキストフィルターデーモンランチャーサービスです。|  
|*種類*|SQLPBENGINE は[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Polybase エンジンサービスです。|  
|*11*|SQLPBDMS は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Polybase データ移動サービスです。|  
|*12*|MSSQLLaunchpad は[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]スタートパッドサービスです。|  
  
## <a name="see-also"></a>参照  
 [サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
