---
title: SetValue メソッド (ClientSettingsGeneralFlag)
ms.custom: seo-lt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetValue Method (ClientSettingsGeneralFlag Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetValue method
ms.assetid: 34443689-a0e0-4668-a811-17532c6fd271
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0c07685bc6848fee979a743865fac0e138ed648d
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85881013"
---
# <a name="setvalue-method-clientsettingsgeneralflag-class"></a>SetValue メソッド (ClientSettingsGeneralFlag クラス)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  参照されたフラグのすべての値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetValue(Value)  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 サーバー設定に使用する一般的なフラグを表す [ClientSettingsGeneralFlag クラス](../../../relational-databases/wmi-provider-configuration-classes/clientsettingsgeneralflag-class/clientsettingsgeneralflag-class.md) オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*Value*|フラグの値を指定するブール値|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 **uint32** 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [クライアント プロトコルの構成](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
