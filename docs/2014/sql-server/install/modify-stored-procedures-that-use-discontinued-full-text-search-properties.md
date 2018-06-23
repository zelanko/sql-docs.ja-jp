---
title: 廃止されたフルテキスト検索プロパティを使用するストアド プロシージャの変更 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- discontinued properties [Full-Text Search]
- stored procedures [Full-Text Search]
ms.assetid: 8d9392d9-a9ba-4378-84e4-59f516b67ddb
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 027fb2a7148dc0948c519836f30c8931d61f610b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077050"
---
# <a name="modify-stored-procedures-that-use-discontinued-full-text-search-properties"></a>廃止されたフルテキスト検索プロパティを使用するストアド プロシージャを変更する
  ストアド プロシージャが正しく実行されるようにするには、既存のプロシージャを編集し、削除または非推奨とされたフルテキスト関連のプロパティおよび設定を削除する必要があります。  
  
## <a name="component"></a>コンポーネント  
 フルテキスト検索  
  
## <a name="description"></a>説明  
 以下のフルテキスト検索関連のプロパティおよび設定が削除されています。  
  
-   **DataTimeout**  
  
-   **ConnectTimeout**  
  
-   **Clean_up**  
  
-   **LogSize**  
  
 以下のフルテキスト検索関連のプロパティおよび設定が削除または非推奨とされています：  
  
-   フルテキスト カタログの "パス"。 フルテキスト カタログは、システムでの特定のファイル パスを持たない論理オブジェクトになります。  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ではデータベースがフルテキスト検索に対して常に既定で有効になっているので、SP_FULLTEXT_DATABASE の有効化/無効化は効力がありません。  
  
## <a name="corrective-action"></a>修正措置  
 お使いのストアド プロシージャを変更して、これらのプロパティを削除してください。  
  
## <a name="see-also"></a>参照  
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  