---
title: ユーザー定義関数は system_function_schema | では許可されていません。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- system functions [SQL Server]
- user-defined functions [SQL Server], system
ms.assetid: 3cb54053-ef65-4558-ae96-8686b6b22f4f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 10813b7bc0a97f0ba8a81f3f48447142659cd596
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66091329"
---
# <a name="user-defined-functions-are-not-allowed-in-system_function_schema"></a>system_function_schema でユーザー定義関数が許可されない
  アップグレードアドバイザーによって、ドキュメントに記載されていないユーザー **system_function_schema**が所有しているユーザー定義関数が検出されました。 このユーザーを指定してユーザー定義のシステム関数を作成することはできません。 **System_function_schema**ユーザー名が存在しません。この名前に関連付けられているユーザー ID (UID = 4) は**sys**スキーマ用に予約されており、内部使用に限定されています。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>[説明]  
 システム オブジェクトの格納とアクセスが次のように変更されました。  
  
-   システムオブジェクトは読み取り専用の**リソース**データベースに格納され、システムオブジェクトを直接更新することはできません。  
  
     システムオブジェクトは、各データベースの**sys**スキーマに論理的に表示されます。 これにより、1 つの要素で構成される関数名を指定してデータベースからシステム関数を呼び出す機能が維持されます。 たとえば、ステートメント `SELECT * FROM fn_helpcollations()` はどのデータベースからでも実行できます。  
  
-   非公開のユーザー **system_function_schema**が削除されました。  
  
-   **System_function_schema**に関連付けられたユーザー ID (UID = 4) は**sys**スキーマ用に予約されており、内部使用のみに制限されています。  
  
 これらの変更によって、ユーザー定義のシステム関数には次の影響があります。  
  
-   **System_function_schema**を参照するデータ定義言語 (DDL) ステートメントは失敗します。 たとえば`CREATE FUNCTION system``function` \_ `schema.fn` 、...\_ `MySystemFunction`成功しません。  
  
-   に[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]アップグレードした後、 **system_function_schema**によって所有されている既存のオブジェクトは、 **master**データベースの**sys**スキーマにのみ格納されます。 システムオブジェクトは変更できないので、 **master**データベースからこれらの関数を変更したり削除したりすることはできません。 また、これらの関数は、1 つの要素だけで構成される関数名を指定して他のデータベースから呼び出すこともできません。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードする前に、以下の作業を完了してください。  
  
1.  **Sp_changeobjectowner**システムストアドプロシージャを使用して、既存のユーザー定義関数の所有権を**dbo**に変更します。  
  
2.  プレフィックス 'fn_' を使用しないように関数名を変更することを検討します。 これにより、現在または今後のシステム関数で名前の競合が発生するのを防ぐことができます。  
  
3.  変更した関数のコピーを、その関数を使用するすべてのデータベースに追加します。  
  
4.  ユーザー定義関数 DDL ステートメントが含まれているすべてのスクリプトで、 **system_function_schema**への参照を**dbo**に置き換えます。  
  
5.  2部構成の名前 dbo を使用するようにこれらの関数を呼び出すスクリプトを変更し**ます。**_function_name_、または3つの部分で構成される名前_database_name_**です。** dbo.*function_name*。  
  
 詳細については、SQL Server オンライン ブックの次のトピックを参照してください。  
  
-   "sp_changeobjectowner"  
  
-   "ユーザーとスキーマの分離"  
  
-   Resource データベース  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)   
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [システムオブジェクトを変更するステートメントを削除します。](../../../2014/sql-server/install/remove-statements-that-modify-system-objects.md)   
 [システム オブジェクトを破棄するステートメントを削除する](../../../2014/sql-server/install/remove-statements-that-drop-system-objects.md)  
  
  
