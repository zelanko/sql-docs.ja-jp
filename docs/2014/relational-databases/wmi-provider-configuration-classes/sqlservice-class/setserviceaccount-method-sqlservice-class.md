---
title: SetServiceAccount メソッド (SqlService クラス) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- SetServiceAccount Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceAccount method
ms.assetid: d5782892-e9d8-4d48-92af-b3afe9610f84
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 74f296fd52640c950d7d2c4b227a1c3aedb17df7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071124"
---
# <a name="setserviceaccount-method-sqlservice-class"></a>SetServiceAccount メソッド (SqlService クラス)
  サーバー インスタンスの実行環境に対応するユーザー名およびパスワードを変更します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.SetServiceAccount(  
ServiceStartName , ServiceStartPassword  
)  
  
```  
  
## <a name="parts"></a>要素  
 *object*  
 サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
 *ServiceStartName*  
 サービスの実行環境に対応するアカウント名を指定する文字列値。 サービスの種類によっては、アカウント名が "ドメイン名\ユーザー名" の形式になる場合もあります。 サービス プロセスの実行時には、ログオンは次のいずれかの形式になります。  
  
-   アカウントがビルトイン ドメインに属している場合、\Username を指定することができます。  
  
-   NULL が指定されている場合、サービスとしてログオンする、 **LocalSystem**アカウント。  
  
 カーネルまたはシステム レベルのドライバーの*StartName*ドライバー オブジェクト名を含む \FileSystem\Rdr または \Driver\Xns、I/O システムが、デバイス ドライバーの読み込みに使用します。 NULL が指定された場合、ドライバーは、I/O システムがサービス名に基づいて作成した既定のオブジェクト名 (たとえば、DWDOM\Admin) で実行されます。  
  
 *ServiceStartPassword*  
 アカウント名のパスワードを指定する文字列値、 *StartName*パラメーター。 パスワードを変更しない場合は NULL を指定します。 サービスがパスワードを持っていない場合は、空の文字列を指定します。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 `uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。 それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [開始して、サービスの停止](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  