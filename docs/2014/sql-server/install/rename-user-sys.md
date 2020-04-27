---
title: ユーザー sys | の名前を変更します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sys user names [SQL Server]
ms.assetid: d622d646-83e4-4b6f-9a21-77b301af04b5
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ce8656df63c9d415ca09b54ecb86b87aba8bd83a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66092858"
---
# <a name="rename-user-sys"></a>ユーザー sys の名前変更が必要
  アップグレードアドバイザーによって、データベースにユーザー名**sys**が検出されました。 この名前は予約されています。 このユーザー名を変更した後、アップグレードしてください。 ユーザー名が変更されていないと、データベースはアップグレード処理後に問題ありの状態となり、データベースをオンラインにするまで使用できません。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 ユーザー **sys**は予約されています。  
  
## <a name="corrective-action"></a>修正措置  
  
### <a name="before-upgrade-procedure"></a>アップグレード前に行う手順  
 をアップグレードする前に、ユーザー **sys**を含む各データベースで、次の操作を行います。  
  
1.  新しいユーザーを作成します。  
  
2.  次のステートメントを使用して、ユーザー **sys**によって付与され、ユーザー **sys**に付与されるすべてのアクセス許可を表示します。  
  
    ```  
    -- Return permissions granted by user sys.  
    SELECT * FROM sysprotects WHERE grantor = USER_ID('sys')  
    -- Return permissions granted to user sys.  
    SELECT * FROM sysprotects WHERE uid = USER_ID('sys')  
    ```  
  
3.  **Sys**が所有するすべてのオブジェクトの所有権を新しいユーザーに転送するには、 **sp_changeobjectowner**を使用します。  
  
4.  ユーザー **sys**を削除します。  
  
5.  手順 2. でキャプチャした元のアクセス許可を復元するには、GRANT ステートメントの AS *new_user*句を使用します。  
  
6.  新しいユーザーを参照するようにスクリプトを修正します。 たとえば、`SELECT * FROM sys.my`_`table` などのステートメントを含むスクリプトを `SELECT * FROM new_user.my_table` に変更する必要があります。  
  
### <a name="after-upgrade-procedure"></a>アップグレード後に行う手順  
 アップグレードの前にユーザー **sys**の名前を変更しなかった場合は、次の手順を実行します。  
  
1.  ステートメント `ALTER DATABASE db_name SET ONLINE` を実行します。 データベースが SINGLE_USER モードになります。  
  
2.  「アップグレード前に行う手順」セクションのすべての手順を実行します。  
  
3.  ステートメント `ALTER DATABASE db_name SET MULTI_USER` を実行します。  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
