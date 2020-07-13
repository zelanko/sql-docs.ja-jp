---
title: マージアーティクルのダミー更新の実行 (レプリケーション Transact-sql プログラミング) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_mergedummyupdate
- dummy updates [SQL Server replication]
ms.assetid: 2f339210-4d85-4843-bd94-e86f7100d3ef
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 07fa0f868b2c3f98496046b138424d7d3a2fa2fd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85010996"
---
# <a name="perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming"></a>マージ アーティクルのダミー更新の実行 (レプリケーション Transact-SQL プログラミング)
  マージ レプリケーションではレプリケーション処理の中でトリガーを使用します。パブリッシュ済みのテーブルに更新が加えられると、更新トリガーが起動します。 WRITETEXT 操作や UPDATETEXT 操作の際など、トリガーを起動せずにデータを更新できる場合もあります。 このような場合、ダミーの UPDATE ステートメントを明示的に追加して、変更をレプリケートする必要があります。 ダミーの UPDATE ステートメントは、レプリケーション ストアド プロシージャを使用して追加できます。  
  
### <a name="to-add-a-dummy-update-statement"></a>ダミーの UPDATE ステートメントを追加するには  
  
1.  ダミーの更新を必要とするマージ パブリッシュ済みテーブルの行に対して、操作 (たとえば UPDATETEXT など) を実行します。  
  
2.  サーバー (パブリッシャーまたはサブスクライバー) 上の変更が加えられたデータベースに対して、[sp_mergedummyupdate &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql) を実行します。 変更が加えられたテーブル **@source_object** と、の変更された行の一意の識別子を指定し **@rowguid** ます。  
  
3.  サブスクリプションを同期して、変更された行をレプリケートします。  
  
  
