---
title: StartMode プロパティ (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- StartMode Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- StartMode property
ms.assetid: c0c2c7f8-d4ae-44f2-ad8e-aecfcb7c2878
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 31d2a413aa606bc6b7065126668fdeabdfacd7b1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73660865"
---
# <a name="startmode-property-sqlservice-class"></a>StartMode プロパティ (SqlService クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  サービスの開始モードを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.StartMode [= value]  
```  
  
## <a name="parts"></a>要素  
 *素材*  
 サービスを表す [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サービスのモードを指定する uint32 値。  
  
 値には、次のいずれかを指定できます。  
  
 ブート  
 値 = 0。 オペレーティング システム ローダーによって開始されるサービスです。 このオプションは、ドライバー サービスにのみ有効です。  
  
 システム  
 値 = 1。 **Ioinitsystem**メソッドによって開始されたサービス。 このオプションは、ドライバー サービスにのみ有効です。  
  
 自動  
 値 = 2。 システムの起動時にサービス コントロール マネージャーによって自動的に開始されるサービスです。  
  
 マニュアル  
 値 = 3。 プロセスが**Startservice**メソッドを呼び出すときに、コンピューターマネージャーによって開始されるサービス。  
  
 無効  
 値 = 4。 サービスを開始できません。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
