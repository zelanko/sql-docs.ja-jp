---
title: SetDefaults メソッド (ServerSettings)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetDefaults Method (ServerSettings Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetDefaults method
ms.assetid: 76e4cfab-4b15-4da4-bb2f-8aac6f927f79
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 86e15376bd56a439e0763e79a5c166d7023125ea
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73660270"
---
# <a name="setdefaults-method-serversettings-class"></a>SetDefaults メソッド (ServerSettings クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  既存のデータを上書きするオプションを使用[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]して、のインスタンスのすべての既定値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetDefaults(OverwriteAll)  
```  
  
## <a name="parts"></a>要素  
 *素材*  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]クライアントインスタンスを表す[serversettings クラス](../../../relational-databases/wmi-provider-configuration-classes/serversettings-class/serversettings-class.md)オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|[説明]|  
|---------------|-----------------|  
|*OverwriteAll*|の[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンスの既存の値を上書きするかどうかを指定するブール値。既存のデータを上書きする場合は**true** 、既存のデータを上書きしない場合は**false**を指定します。|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 U**int32**値。サービスが正常に変更された場合は0、要求がサポートされていない場合は1になり、それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
