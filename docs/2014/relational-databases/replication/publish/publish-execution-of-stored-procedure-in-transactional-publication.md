---
title: トランザクションパブリケーションでのストアドプロシージャの実行のパブリッシュ (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a226d7c58b3b72caf415d8e873b58ca38d3c749f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85060425"
---
# <a name="publish-the-execution-of-a-stored-procedure-in-a-transactional-publication-sql-server-management-studio"></a>トランザクション パブリケーションでのストアド プロシージャの実行のパブリッシュ (SQL Server Management Studio)
  (単なる定義ではなく) ストアドプロシージャの実行を [**アーティクルのプロパティ- \<Article> ** ] ダイアログボックスでパブリッシュするように指定します。 このダイアログボックスは、パブリケーションの新規作成ウィザードおよび [**パブリケーションのプロパティ \<Publication> -** ] ダイアログボックスで使用できます。 ウィザードの使用およびダイアログ ボックスへのアクセスの詳細については、「[パブリケーションの作成](create-a-publication.md)」および「[View and Modify Publication Properties](view-and-modify-publication-properties.md)」 (パブリケーション プロパティの表示および変更) を参照してください。  
  
 プロシージャの定義 (CREATE PROCEDURE ステートメント) はサブスクリプションが初期化されるときにサブスクライバーにレプリケートされます。プロシージャがパブリッシャーで実行されるときに、レプリケーションは対応するプロシージャをサブスクライバーで実行します。  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a>ストアド プロシージャの実行をパブリッシュするには  
  
1.  パブリケーションの新規作成ウィザードまたは [**パブリケーションのプロパティ- \<Publication> ** ] ダイアログボックスの [**アーティクル**] ページで、ストアドプロシージャを選択します。  
  
2.  **[アーティクルのプロパティ]** をクリックしてから、 **[反転表示されたストアド プロシージャのプロパティを設定]** をクリックします。  
  
3.  [**アーティクルのプロパティ- \<Article> ** ] ダイアログボックスで、 **Replicate**オプションに次のいずれかの値を指定します。  
  
    -   **[ストアド プロシージャの実行]**  
  
    -   **SP のシリアル化されたトランザクションでの実行**  
  
         これは、推奨オプションです。このオプションを指定すると、プロシージャがシリアル化可能なトランザクションのコンテキスト内で実行される場合にのみ、プロシージャの実行がレプリケートされます。 ストアド プロシージャがシリアル化可能なトランザクションの外から実行される場合、パブリッシュされたテーブルのデータに対する変更は一連の DML (データ操作言語) ステートメントとしてレプリケートされます。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  [**パブリケーションのプロパティ- \<Publication> ** ] ダイアログボックスが表示されている場合は、[ **OK** ] をクリックして保存し、ダイアログボックスを閉じます。  
  
## <a name="see-also"></a>参照  
 [トランザクションレプリケーションでのストアドプロシージャの実行のパブリッシュ](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  
