---
title: MSSQLSERVER_33129 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33129 (Database Engine error)
ms.assetid: 83b5f368-f1a1-4a40-9bb6-c77e2dec690f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 60be94308520f93c76f28ef5e0d1bbbf474dfdbd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48063739"
---
# <a name="mssqlserver33129"></a>MSSQLSERVER_33129
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|33129|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SEC_CANNOT_DISABLE_WIN_GROUP|  
|メッセージ テキスト|ALTER_LOGIN を DISABLE 引数と共に使用して Windows グループへのアクセスを拒否することはできません。|  
  
## <a name="explanation"></a>説明  
 このメッセージは、Windows グループのログインを無効にしようとしたときに発生します。  
  
## <a name="user-action"></a>ユーザーの操作  
 Windows グループのログインを無効にすることはできません。 Windows グループに許可されているアクセス権限を一時的に削除するには、Windows グループのログインの CONNECT 権限を REVOKE (取り消し) します。 この場合、Windows ユーザーは個人のログインまたは別の Windows グループを介してアクセスできる可能性があります。 次の例では、WESTCOAST ドメインの Accounting グループに対する CONNECT 権限を取り消します。  
  
```tsql  
REVOKE CONNECT TO [WESTCOAST\Accounting];  
```  
  
  
