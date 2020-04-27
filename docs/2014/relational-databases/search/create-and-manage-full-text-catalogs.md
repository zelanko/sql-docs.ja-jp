---
title: フルテキスト カタログの作成と管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs [SQL Server], creating
- full-text search [SQL Server], using SQL Server Management Studio
ms.assetid: 824b7131-44a6-4815-89e6-62b7bab060e3
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d90ba7f8e183beeeeefe25ea20834b07d7a1bf80
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66011470"
---
# <a name="create-and-manage-full-text-catalogs"></a>フルテキスト カタログの作成と管理
  フルテキスト カタログが、ファイル グループに属さない仮想オブジェクトとなりました。これは、フルテキスト インデックスのグループを指す論理的概念です。  
  
##  <a name="creating-a-full-text-catalog"></a><a name="creating"></a>フルテキストカタログの作成  
  
#### <a name="to-create-a-full-text-catalog"></a>フルテキスト カタログを作成するには  
  
1.  オブジェクト エクスプローラーで、サーバーを展開し、 **[データベース]** を展開して、フルテキスト カタログを作成する対象のデータベースを展開します。  
  
2.  **[ストレージ]** を展開し、 **[フルテキスト カタログ]** を右クリックします。  
  
3.  **[新しいフルテキスト カタログ]** を選択します。  
  
4.  **[新しいフルテキスト カタログ]** ダイアログ ボックスで、再作成するカタログの情報を指定します。 詳細については、「[[新しいフルテキスト カタログ] &#40;[全般] ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)」を参照してください。  
  
    > [!NOTE]  
    >  フルテキスト カタログ ID は、00005 から始まり、新しいカタログが作成されるたびに 1 ずつ増加します。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
  
##  <a name="viewing-the-properties-of-a-full-text-catalog"></a><a name="props"></a>フルテキストカタログのプロパティの表示  
 FULLTEXTCATALOGPROPERTY などの [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数は、フルテキスト インデックスに関連するさまざまなプロパティの値を取得するために使用できます。 この情報は、フルテキスト検索の管理およびトラブルシューティングに役立ちます。  
  
 次の表は、フルテキスト カタログに関連しているプロパティを示しています。  
  
|プロパティ|説明|機能|  
|--------------|-----------------|--------------|  
|`AccentSensitivity`|アクセントの区別の設定。|[FULLTEXTCATALOGPROPERTY](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql)|  
|`ImportStatus`|フルテキスト カタログがインポートされているかどうかを示します。|FULLTEXTCATALOGPROPERTY|  
|`IndexSize`|フルテキスト カタログのサイズ (MB 単位)。|FULLTEXTCATALOGPROPERTY|  
|`ItemCount`|現在フルテキスト カタログ内にあるフルテキスト インデックス項目の数。|FULLTEXTCATALOGPROPERTY|  
|`MergeStatus`|マスター マージの実行状況を示します。|FULLTEXTCATALOGPROPERTY|  
|`PopulateCompletionAge`|01/01/1990 00:00:00 から、最後のフルテキスト インデックス作成が完了した時刻までの時間 (秒単位)。|FULLTEXTCATALOGPROPERTY|  
|`PopulateStatus`|作成状態。<br /><br /> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|FULLTEXTCATALOGPROPERTY|  
|`UniqueKeyCount`|フルテキスト カタログ内にある一意のキーの数。|FULLTEXTCATALOGPROPERTY|  
  
  
  
##  <a name="rebuilding-a-full-text-catalog"></a><a name="rebuildone"></a>フルテキストカタログの再構築  
  
#### <a name="to-rebuild-a-full-text-catalog"></a>フルテキスト カタログを再構築するには  
  
1.  オブジェクト エクスプローラーで、サーバーを展開し、 **[データベース]** を展開して、再構築するフルテキスト カタログが格納されているデータベースを展開します。  
  
2.  **[ストレージ]** を展開し、 **[フルテキスト カタログ]** を展開します。  
  
3.  再構築するフルテキスト カタログの名前を右クリックし、 **[再構築]** を選択します。  
  
4.  **"フルテキスト カタログを削除して再構築しますか?"** という確認メッセージが表示されたら、 **[OK]** をクリックします。  
  
5.  **[フルテキスト カタログの再構築]** ダイアログ ボックスで、 **[閉じる]** をクリックします。  
  
  
  
##  <a name="rebuilding-all-full-text-catalogs-for-a-database"></a><a name="rebuildall"></a>データベースのすべてのフルテキストカタログの再構築  
  
#### <a name="to-rebuild-the-full-text-catalogs-for-a-database"></a>データベースのフルテキスト カタログを再構築するには  
  
1.  オブジェクト エクスプローラーで、サーバーを展開し、 **[データベース]** を展開して、再構築するフルテキスト カタログが格納されているデータベースを展開します。  
  
2.  **[ストレージ]** を展開し、 **[フルテキスト カタログ]** を右クリックします。  
  
3.  **[すべて再構築]** を選択します。  
  
4.  **[すべてのフルテキスト カタログを削除して再構築しますか?]** という確認メッセージが表示されたら、 **[OK]** をクリックします。  
  
5.  **[すべてのフルテキスト カタログの再構築]** ダイアログ ボックスで、 **[閉じる]** をクリックします。  
  
  
  
##  <a name="removing-a-full-text-catalog-from-a-database"></a><a name="removing"></a>データベースからのフルテキストカタログの削除  
  
#### <a name="to-remove-a-full-text-catalog-from-a-database"></a>データベースからフルテキスト カタログを削除するには  
  
1.  オブジェクト エクスプローラーで、サーバーを展開し、 **[データベース]** を展開して、削除するフルテキスト カタログを含むデータベースを展開します。  
  
2.  **[ストレージ]** を展開し、 **[フルテキスト カタログ]** を展開します。  
  
3.  削除するフルテキスト カタログを右クリックし、 **[削除]** を選択します。  
  
4.  **[オブジェクトの削除]** ダイアログ ボックスで **[OK]** をクリックします。  
  
  
  
## <a name="see-also"></a>参照  
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)  
  
  
