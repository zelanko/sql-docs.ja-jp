---
description: SetServiceAccount メソッド (SqlService クラス)
title: SetServiceAccount メソッド (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetServiceAccount Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetServiceAccount method
ms.assetid: d5782892-e9d8-4d48-92af-b3afe9610f84
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 898d6a1eae5cf82915bc4647690b3ce991aa3352
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460041"
---
# <a name="setserviceaccount-method-sqlservice-class"></a>SetServiceAccount メソッド (SqlService クラス)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  サーバー インスタンスの実行環境に対応するユーザー名およびパスワードを変更します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetServiceAccount(ServiceStartName , ServiceStartPassword)  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 サービスを表す [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
 *ServiceStartName*  
 サービスの実行環境に対応するアカウント名を指定する文字列値。 サービスの種類によっては、アカウント名が "ドメイン名\ユーザー名" の形式になる場合もあります。 サービス プロセスの実行時には、ログオンは次のいずれかの形式になります。  
  
-   アカウントがビルトイン ドメインに属している場合、\Username を指定することができます。  
  
-   NULL を指定した場合、サービスは **LocalSystem** アカウントとしてログオンします。  
  
 カーネルまたはシステムレベルのドライバーの場合、 *StartName* にはドライバーオブジェクト名 (\ Filesystem\r dr または \Driver\Xns) が含まれます。この名前は、i/o システムがデバイスドライバーを読み込むために使用します。 NULL が指定された場合、ドライバーは、I/O システムがサービス名に基づいて作成した既定のオブジェクト名 (たとえば、DWDOM\Admin) で実行されます。  
  
 *ServiceStartPassword*  
 *StartName*パラメーターのアカウント名のパスワードを示す文字列値です。 パスワードを変更しない場合は NULL を指定します。 サービスがパスワードを持っていない場合は、空の文字列を指定します。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 **Uint32**値。サービスが正常に変更された場合は0、要求がサポートされていない場合は1になります。 それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
