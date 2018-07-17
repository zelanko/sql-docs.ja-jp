---
title: トランザクション パブリケーションでのストアド プロシージャの実行 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 273873f2e208c1be3d3b2fbd59a4b0e25efbbdb1
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37349204"
---
# <a name="publish-execution-of-stored-procedure-in-transactional-publication"></a>トランザクション パブリケーションでのストアド プロシージャの実行
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  ストアド プロシージャの単なる定義ではなく、その実行をパブリッシュするように、**[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスで指定できます。 このダイアログ ボックスは、パブリケーションの新規作成ウィザードおよび **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスで使用できます。 ウィザードの使用およびダイアログ ボックスへのアクセスの詳細については、「[パブリケーションの作成](../../../relational-databases/replication/publish/create-a-publication.md)」および「[View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」 (パブリケーション プロパティの表示および変更) を参照してください。  
  
 プロシージャの定義 (CREATE PROCEDURE ステートメント) はサブスクリプションが初期化されるときにサブスクライバーにレプリケートされます。プロシージャがパブリッシャーで実行されるときに、レプリケーションは対応するプロシージャをサブスクライバーで実行します。  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a>ストアド プロシージャの実行をパブリッシュするには  
  
1.  パブリケーションの新規作成ウィザードまたは **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[アーティクル]** ページで、ストアド プロシージャを選択します。  
  
2.  **[アーティクルのプロパティ]** をクリックしてから、 **[反転表示されたストアド プロシージャのプロパティを設定]** をクリックします。  
  
3.  **[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスで、**[レプリケート]** オプションの次のいずれかの値を指定します。  
  
    -   **[ストアド プロシージャの実行]**  
  
    -   **[SP のシリアル化されたトランザクションでの実行]**  
  
         これは、推奨オプションです。このオプションを指定すると、プロシージャがシリアル化可能なトランザクションのコンテキスト内で実行される場合にのみ、プロシージャの実行がレプリケートされます。 ストアド プロシージャがシリアル化可能なトランザクションの外から実行される場合、パブリッシュされたテーブルのデータに対する変更は一連の DML (データ操作言語) ステートメントとしてレプリケートされます。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスが表示されている場合は、**[OK]** をクリックして保存し、ダイアログ ボックスを閉じます。  
  
## <a name="see-also"></a>参照  
 [トランザクション レプリケーションにおけるパブリッシング ストアド プロシージャの実行](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  
