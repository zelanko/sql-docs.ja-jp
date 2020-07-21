---
title: SqlServiceType プロパティ (Sqlserviceadvanced Property クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SqlServiceType Property (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SqlServiceType property
ms.assetid: 20f1663a-9a14-4f14-8c1b-8aa133e272c3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 17bbcb7e1311d64de518324707c597b7471a40a8
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061332"
---
# <a name="sqlservicetype-property-sqlserviceadvancedproperty-class"></a>SqlServiceType プロパティ (SqlServiceAdvancedProperty クラス)
  詳細プロパティに関連付けられたマネージド サービスの型を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.SetBoolValue(  
NumValue  
)  
  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 詳細プロパティを表す [SqlServiceAdvancedProperty クラス](sqlserviceadvancedproperty-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスの種類を指定する uint32 値。  
  
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
  
## <a name="see-also"></a>参照  
 [サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
