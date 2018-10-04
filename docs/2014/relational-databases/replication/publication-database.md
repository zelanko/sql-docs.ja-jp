---
title: パブリケーション データベース | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.publicationdatabase.f1
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e006186ef330c51644e848fb1aad2cfa3b85a2d3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48204182"
---
# <a name="publication-database"></a>パブリケーション データベース
  パブリケーション データベースは、レプリケートされるデータおよびデータベース オブジェクトの供給元として機能する、パブリッシャー上のデータベースです。 レプリケーションに使用される各パブリケーション データベースは有効である必要があります。 データベースは、 **sysadmin** 固定サーバー ロールのメンバーが次のことを行う場合に有効です。  
  
-   パブリケーションの新規作成ウィザードを使用してデータベースにパブリケーションを作成します。  
  
-   **[パブリッシャーのプロパティ]** ダイアログ ボックスでデータベースを選択します。  
  
-   **sp_replicationdboption** を実行し、オプションの **publish** (スナップショット用またはトランザクション パブリケーション用) または **merge publish** (マージ パブリケーション用) を **True**に設定します。  
  
## <a name="options"></a>および  
 **データベース**  
 パブリッシュするデータおよびデータベース オブジェクトを含むデータベースの名前を選択します。  
  
## <a name="see-also"></a>参照  
 [データとデータベース オブジェクトのパブリッシュ](publish/publish-data-and-database-objects.md)   
 [Create a Publication](publish/create-a-publication.md)   
 [View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](view-and-modify-distributor-and-publisher-properties.md)   
 [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)  
  
  
