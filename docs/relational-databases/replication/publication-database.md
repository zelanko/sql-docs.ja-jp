---
description: パブリケーション データベース
title: パブリケーション データベース | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.publicationdatabase.f1
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: ce56be1b0c8c2b647d93ac01f9adbc9d5aa9ba44
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2020
ms.locfileid: "97460195"
---
# <a name="publication-database"></a>パブリケーション データベース
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  パブリケーション データベースは、レプリケートされるデータおよびデータベース オブジェクトの供給元として機能する、パブリッシャー上のデータベースです。 レプリケーションに使用される各パブリケーション データベースは有効である必要があります。 データベースは、 **sysadmin** 固定サーバー ロールのメンバーが次のことを行う場合に有効です。  
  
-   パブリケーションの新規作成ウィザードを使用してデータベースにパブリケーションを作成します。  
  
-   **[パブリッシャーのプロパティ]** ダイアログ ボックスでデータベースを選択します。  
  
-   **sp_replicationdboption** を実行し、オプションの **publish** (スナップショット用またはトランザクション パブリケーション用) または **merge publish** (マージ パブリケーション用) を **True** に設定します。  
  
## <a name="options"></a>オプション  
 **データベース**  
 パブリッシュするデータおよびデータベース オブジェクトを含むデータベースの名前を選択します。  
  
## <a name="see-also"></a>参照  
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_replicationdboption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)  
  
  
