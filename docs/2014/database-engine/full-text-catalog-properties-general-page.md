---
title: フルテキスト カタログのプロパティ ([全般] ページ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-search
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.general.f1
ms.assetid: d1f66762-2d40-4f24-b635-a417d22ee79a
caps.latest.revision: 34
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: fc774b0dfd87ae4f63e9332dd6813d92f79e4a5c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176011"
---
# <a name="full-text-catalog-properties-general-page"></a>[フルテキスト カタログのプロパティ] ([全般] ページ)
  ここでは、 **[フルテキスト カタログのプロパティ]** ダイアログ ボックスの **[全般]** ページに表示されるオプションと機能を示します。  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]データベース、フルテキスト カタログは、フルテキスト インデックスのグループを参照する論理的概念です。 フルテキスト カタログは、ファイル グループに属さない仮想オブジェクトです。  
  
## <a name="options"></a>および  
  
### <a name="properties"></a>[プロパティ]  
 **既定のカタログ**  
 カタログがデータベースの既定のカタログかどうかを示します。  
  
 **作成状態**  
 カタログの状態を示します。 有効な値は次のとおりです。  
  
-   **アイドル状態します。**  
  
-   **クロール中**  
  
-   **一時停止**  
  
-   **調整**  
  
-   **回復します。**  
  
-   **シャットダウン**  
  
-   **増分作成が進行中**  
  
-   **インデックスの構築**  
  
-   **ディスクがいっぱいで、一時停止**  
  
-   **Change tracking**  
  
 **項目数**  
 カタログ内のフルテキスト項目の数を表示します。  
  
 **カタログのサイズ**  
 フルテキスト カタログのサイズ (MB) が表示されます。  
  
 **Name**  
 フルテキスト カタログの名前です。  
  
 **アクセントの区別**  
 チルダ (**~**)、アキュート アクセント記号 (**´**)、ウムラウト (**¨**) などの分音記号をカタログで区別するかしないかを表示または変更します。 有効な値は、  
  
-   **いいえ**  
  
-   **はい**  
  
-   分音記号については、次を参照してください。[分音記号](http://go.microsoft.com/fwlink/?LinkId=154091)MSN エンカルタ百科事典にします。  
  
 **最終作成日付**  
 そのカタログの最後に作成された日付を表示します。  
  
 **[所有者]**  
 フルテキスト カタログの所有者です。  
  
 **一意なキー数**  
 このカタログの中でフルテキスト インデックスを構成している一意な文字列の個数です。  
  
### <a name="catalog-action"></a>カタログ アクション  
  
|||  
|-|-|  
|**なし**|**[カタログを最適化する]**、 **[カタログを再構築する]**、または **[カタログを再作成する]** の操作を実行しません。|  
|**カタログを最適化します。**|カタログの使用効率を最適化し、クエリ パフォーマンスを向上させます。 また、検索結果の関連順位の正確さを向上させます。<br /><br /> このアクションでは、ALTER FULLTEXT CATALOG *catalog_name* REORGANIZE が実行されます。|  
|**カタログを再構築します。**|フルテキスト カタログを削除して再構築します。 アクセントの区別など基本的なカタログ プロパティが変更された場合は、この操作を実行する必要があります。<br /><br /> 再構築を成功させるために、フルテキスト カタログが存在するファイル グループは、オンラインで読み書きできる必要があります。 再構築の後で、フルテキスト インデックスは再作成されます。<br /><br /> このアクションでは、ALTER FULLTEXT CATALOG *catalog_name* REBUILD が実行されます。|  
|**カタログを再作成します。**|データへの最新の変更によりカタログを更新します。 このオプションは、カタログ ダウンタイムを必要とします。|  
  
## <a name="see-also"></a>参照  
 [フルテキスト インデックスの作成](../relational-databases/indexes/indexes.md)  
  
  