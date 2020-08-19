---
description: SetValue メソッド (ServerSettingsGeneralFlag クラス)
title: SetValue メソッド (ServerSettingsGeneralFlag)
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetValue Method (ServerSettingsGeneralFlag Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetValue method
ms.assetid: a889feac-c0e0-4635-b506-843863d86967
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e400d07a8e14bed9337cd0e889cb6ca13b44f674
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88427274"
---
# <a name="setvalue-method-serversettingsgeneralflag-class"></a>SetValue メソッド (ServerSettingsGeneralFlag クラス)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  参照されたフラグのすべての値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetValue(Value)  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 サーバー設定に使用する一般的なフラグを表す [ServerSettingsGeneralFlag クラス](../../../relational-databases/wmi-provider-configuration-classes/serversettingsgeneralflag-class/serversettingsgeneralflag-class.md) オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*Value*|フラグの値を指定するブール値|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 **uint32** 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
