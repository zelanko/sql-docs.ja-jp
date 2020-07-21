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
ms.openlocfilehash: 6818c721d6f555ea2cf8e03aa7ed664fe10c04cd
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85888337"
---
# <a name="sqlservicetype-property-sqlservice-class"></a>SqlServiceType プロパティ (SqlService クラス)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  マネージド サービスの種類を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SqlServiceType [= value]  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 サービスを表す [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サービスの種類を指定する uint32 値 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。  
  
## <a name="remarks"></a>Remarks  
 戻り値は次のいずれかです。  
  
|Type|定義|  
|----------|----------------|  
|*1*|MSSQLSERVER は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスです。|  
|*2*|SQLSERVERAGENT は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント サービスです。|  
|*3*|MSFTESQL は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フルテキスト検索エンジン サービスです。|  
|*4*|MsDtsServer は [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] サービスです。|  
|*5*|MSSQLServerOLAPService は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サービスです。|  
|*6*|ReportServer は [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] サービスです。|  
|*7*|SQLBrowser は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser サービスです。|  
|*8*|Nsservice.exe は [!INCLUDE[ssNoVersion](../../../includes/ssns-md.md)] Notification service です。|  
|*9*|MSSQLFDLauncher は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フルテキストフィルターデーモンランチャーサービスです。|  
|"*10*"|SQLPBENGINE は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Polybase エンジンサービスです。|  
|*11*|SQLPBDMS は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Polybase データ移動サービスです。|  
|*12*|MSSQLLaunchpad は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] スタートパッドサービスです。|  
  
## <a name="see-also"></a>関連項目  
 [サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
