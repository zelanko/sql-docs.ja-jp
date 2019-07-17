---
title: SqlServiceType プロパティ (SqlService クラス) |Microsoft Docs
ms.custom: ''
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
ms.openlocfilehash: f7b8b0d47a3778303cfcbd234add3167f6c225bb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68054765"
---
# <a name="sqlservicetype-property-sqlservice-class"></a>SqlServiceType プロパティ (SqlService クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  マネージド サービスの種類を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SqlServiceType [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 サービスを表す [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 指定する uint32 値、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]サービスの種類。  
  
## <a name="remarks"></a>コメント  
 戻り値は次のいずれかです。  
  
|種類|定義|  
|----------|----------------|  
|*1*|MSSQLSERVER は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスです。|  
|*2*|SQLSERVERAGENT は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント サービスです。|  
|*3*|MSFTESQL は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フルテキスト検索エンジン サービスです。|  
|*4*|MsDtsServer は [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] サービスです。|  
|*5*|MSSQLServerOLAPService は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サービスです。|  
|*6*|ReportServer は [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] サービスです。|  
|*7*|SQLBrowser は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser サービスです。|  
|*8*|NsService は、[!INCLUDE[ssNoVersion](../../../includes/ssns-md.md)]通知サービス。|  
|*9*|MSSQLFDLauncher は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]フルテキスト フィルター デーモン ランチャー サービス。|  
|"*10*"|SQLPBENGINE は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Polybase エンジン サービス。|  
|*11*|SQLPBDMS は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Polybase Data Movement サービス。|  
|*12*|MSSQLLaunchpad は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]スタート パッド サービス。|  
  
## <a name="see-also"></a>関連項目  
 [開始とサービスの停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
