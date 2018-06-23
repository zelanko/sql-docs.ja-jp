---
title: SQL Server Native Client Support for LocalDB |Microsoft ドキュメント
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
ms.assetid: 127569d1-a9f7-49bf-a561-c084986a8871
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 144fe940cd1be0c2338e4e874658738b8854583d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164068"
---
# <a name="sql-server-native-client-support-for-localdb"></a>SQL Server Native Client における LocalDB のサポート
  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 以降、SQLServer の簡易バージョンである LocalDB を使用できるようになります。 ここでは、LocalDB インスタンス内のデータベースに接続する方法について説明します。  
  
## <a name="remarks"></a>コメント  
 LocalDB のインストール方法や LocalDB インスタンスの構成方法など、LocalDB の詳細については、以下を参照してください。  
  
-   [SQL Server Express LocalDB リファレンス](../../sql-server-express-localdb-reference.md)  
  
-   [SQL Server 2014 Express LocalDB](../../../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
 要約すると、LocalDB では次の操作を実行できます。  
  
-   `sqllocaldb.exe i` を使用して既定のインスタンスの名前を検出できます。  
  
-   `AttachDBFilename` 接続文字列キーワードを使用して、サーバーをアタッチするデータベース ファイルを指定できます。 使用する場合`AttachDBFilename`を持つデータベースの名前を指定しない場合は、**データベース**接続文字列キーワードでは、アプリケーションを閉じるときに、データベースは LocalDB インスタンスから削除されます。  
  
-   接続文字列では、次のように LocalDB インスタンスを指定します。  
  
```  
SERVER=(localdb)\v11.0  
```  
  
 必要に応じて、sqllocaldb.exe を使用して LocalDB インスタンスを作成できます。 また、sqlcmd.exe を使用して、LocalDB インスタンスのデータベースの追加と変更を実行できます。 たとえば、 `sqlcmd -S (localdb)\v11.0`のようにします。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](sql-server-native-client-features.md)  
  
  