---
title: "SetServiceAccount メソッド (SqlService クラス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- SetServiceAccount Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetServiceAccount method
ms.assetid: d5782892-e9d8-4d48-92af-b3afe9610f84
caps.latest.revision: 
author: JennieHubbard
ms.author: jhubbard
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1bdcb3f6789baf009165a74bcf3d82630fa868fd
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="setserviceaccount-method-sqlservice-class"></a>SetServiceAccount メソッド (SqlService クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
サーバー インスタンスの実行環境に対応するユーザー名およびパスワードを変更します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetServiceAccount(ServiceStartName , ServiceStartPassword)  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 サービスを表す [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
 *ServiceStartName*  
 サービスの実行環境に対応するアカウント名を指定する文字列値。 サービスの種類によっては、アカウント名が "ドメイン名\ユーザー名" の形式になる場合もあります。 サービス プロセスの実行時には、ログオンは次のいずれかの形式になります。  
  
-   アカウントがビルトイン ドメインに属している場合、\Username を指定することができます。  
  
-   NULL が指定されている場合、サービスとしてログオンする、 **LocalSystem**アカウント。  
  
 カーネルまたはシステム レベルのドライバーの*StartName*ドライバー オブジェクト名を含む \FileSystem\Rdr または \Driver\Xns、I/O システムが、デバイス ドライバーの読み込みに使用します。 NULL が指定された場合、ドライバーは、I/O システムがサービス名に基づいて作成した既定のオブジェクト名 (たとえば、DWDOM\Admin) で実行されます。  
  
 *ServiceStartPassword*  
 アカウント名のパスワードを指定する文字列値、 *StartName*パラメーター。 パスワードを変更しない場合は NULL を指定します。 サービスがパスワードを持っていない場合は、空の文字列を指定します。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 A **uint32**値は、サービスが正常に変更された場合は 0 または 1 の場合は、要求はサポートされていません。 それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [開始して、サービスの停止](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
