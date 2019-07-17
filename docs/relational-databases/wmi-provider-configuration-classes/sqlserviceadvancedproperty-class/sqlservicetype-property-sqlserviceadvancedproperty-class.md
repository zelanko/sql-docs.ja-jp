---
title: SqlServiceType プロパティ (SqlServiceAdvancedProperty クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SqlServiceType Property (SqlServiceAdvancedProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SqlServiceType property
ms.assetid: 20f1663a-9a14-4f14-8c1b-8aa133e272c3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 30b69a61f184738f72fce32920d8aeedd62797eb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68139460"
---
# <a name="sqlservicetype-property-sqlserviceadvancedproperty-class"></a>SqlServiceType プロパティ (SqlServiceAdvancedProperty クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  詳細プロパティに関連付けられたマネージド サービスの型を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetBoolValue(NumValue)  
```  
  
## <a name="parts"></a>要素  
 *object*  
 詳細プロパティを表す [SqlServiceAdvancedProperty クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスの種類を指定する uint32 値。  
  
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
  
  
