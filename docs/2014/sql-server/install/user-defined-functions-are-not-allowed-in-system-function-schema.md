---
title: ユーザー定義関数は system_function_schema では許可されません |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- system functions [SQL Server]
- user-defined functions [SQL Server], system
ms.assetid: 3cb54053-ef65-4558-ae96-8686b6b22f4f
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 16c6cf618028d56a3b09cdad8da4cfd9eb9309f4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36082898"
---
# <a name="user-defined-functions-are-not-allowed-in-systemfunctionschema"></a>system_function_schema でユーザー定義関数が許可されない
  アップグレード アドバイザーに記載されていないユーザーが所有するユーザー定義関数が検出された**system_function_schema**です。 このユーザーを指定してユーザー定義のシステム関数を作成することはできません。 **System_function_schema**ユーザー名が存在しないため、この名前に関連付けられているユーザー ID (UID = 4) 用に予約されて、 **sys**スキーマし、内部使用のみに限定します。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 システム オブジェクトの格納とアクセスが次のように変更されました。  
  
-   システム オブジェクトが、読み取り専用に格納されている**リソース**データベースし、直接システム オブジェクトの更新が許可されていません。  
  
     システム オブジェクトは論理的に表示される、 **sys**すべてのデータベースのスキーマです。 これにより、1 つの要素で構成される関数名を指定してデータベースからシステム関数を呼び出す機能が維持されます。 たとえば、ステートメント `SELECT * FROM fn_helpcollations()` はどのデータベースからでも実行できます。  
  
-   ドキュメント化されていないユーザー **system_function_schema**は削除されました。  
  
-   ID に関連付けられているユーザー **system_function_schema** (UID = 4) 用に予約されて、 **sys**スキーマし、内部使用のみに限定します。  
  
 これらの変更によって、ユーザー定義のシステム関数には次の影響があります。  
  
-   データ定義言語 (DDL) ステートメントを参照する**system_function_schema**は失敗します。 たとえば、ステートメント`CREATE FUNCTION system`_`function` \_ `schema.fn` \_ `MySystemFunction`しています. 成功しません。  
  
-   アップグレードした後[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、既存のオブジェクトによって所有されている**system_function_schema**のみに含まれます、 **sys**のスキーマ、**マスター**データベース。 これらの関数を変更またはから削除するシステム オブジェクトが変更されることはできません、ためは決して、**マスター**データベース。 また、これらの関数は、1 つの要素だけで構成される関数名を指定して他のデータベースから呼び出すこともできません。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードする前に、以下の作業を完了してください。  
  
1.  既存のユーザー定義関数の所有権を変更**dbo**を使用して、 **sp_changeobjectowner**システム ストアド プロシージャです。  
  
2.  プレフィックス 'fn_' を使用しないように関数名を変更することを検討します。 これにより、現在または今後のシステム関数で名前の競合が発生するのを防ぐことができます。  
  
3.  変更した関数のコピーを、その関数を使用するすべてのデータベースに追加します。  
  
4.  参照を置き換える**system_function_schema**で**dbo**ユーザー定義関数 DDL ステートメントが含まれているすべてのスクリプトでします。  
  
5.  これらの関数を使用するか、2 部構成の名前 dbo * を呼び出すスクリプトを変更して *. * * * function_name*、または 3 部構成の名前*database_name ***.** dbo します。* function_name * です。  
  
 詳細については、SQL Server オンライン ブックの次のトピックを参照してください。  
  
-   "sp_changeobjectowner"  
  
-   「ユーザーとスキーマの分離」  
  
-   Resource データベース  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)   
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [システム オブジェクトを変更するステートメントを削除します。](../../../2014/sql-server/install/remove-statements-that-modify-system-objects.md)   
 [システム オブジェクトを削除するステートメントを削除します。](../../../2014/sql-server/install/remove-statements-that-drop-system-objects.md)  
  
  
