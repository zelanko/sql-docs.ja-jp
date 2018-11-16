---
title: SetDefaults メソッド (CInstance クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetDefaults Method (CInstance Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetDefaults method
ms.assetid: ed9e99c2-3e28-4ee8-bc20-61ca05984973
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 021d213ac83c02be7811fa3b5ea1ec470dfd527e
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51664332"
---
# <a name="cinstance-class---setdefaults-method"></a>CInstance クラス - SetDefaults メソッド
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  インスタンスのすべての既定値の設定、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]既存のデータを上書きするオプションを使用するクライアント。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetDefaults(OverwriteAll)  
```  
  
## <a name="parts"></a>要素  
 *object*  
 [クライアント インスタンスを表す](../../relational-databases/wmi-provider-configuration-classes/cinstance-class.md) CInstance クラス [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*OverwriteAll*|インスタンス上の既存の値を上書きするかどうかを指定するブール値、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント: **true**既存のデータを上書きするか、 **false**既存のデータを上書きしない場合。|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 **uint32** 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [クライアント プロトコルの構成](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
