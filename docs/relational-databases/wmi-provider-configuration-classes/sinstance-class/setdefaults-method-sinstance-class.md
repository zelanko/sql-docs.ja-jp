---
title: SetDefaults メソッド (SInstance)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetDefaults Method (SInstance Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetDefaults method
ms.assetid: dc3c6a85-0711-4688-bf4f-91168c57af28
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 346c714dea89d171431527dfa42e8503aa30e5f4
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85888513"
---
# <a name="setdefaults-method-sinstance-class"></a>SetDefaults メソッド (SInstance クラス)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 既存のデータを上書きするオプションを使用して、のインスタンスのすべての既定値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetDefaults(OverwriteAll)  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 サーバーインスタンスを表す[Sinstance クラス](../../../relational-databases/wmi-provider-configuration-classes/sinstance-class/sinstance-class.md)オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*OverwriteAll*|クライアントのインスタンスの既存の値を上書きするかどうかを指定するブール値 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] です。既存のデータが上書きされる場合は**true** 、既存のデータが上書きされない場合は**false**になります。|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 **uint32** 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
