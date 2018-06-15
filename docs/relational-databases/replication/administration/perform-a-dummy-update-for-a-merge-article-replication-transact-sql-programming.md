---
title: マージ アーティクルのダミー更新の実行 (レプリケーション T-SQL プログラミング) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_mergedummyupdate
- dummy updates [SQL Server replication]
ms.assetid: 2f339210-4d85-4843-bd94-e86f7100d3ef
caps.latest.revision: 31
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: eea3359fa0c0d3cbf91621277ce2737bbb5fc60b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32952917"
---
# <a name="perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming"></a>マージ アーティクルのダミー更新の実行 (レプリケーション Transact-SQL プログラミング)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  マージ レプリケーションではレプリケーション処理の中でトリガーを使用します。パブリッシュ済みのテーブルに更新が加えられると、更新トリガーが起動します。 WRITETEXT 操作や UPDATETEXT 操作の際など、トリガーを起動せずにデータを更新できる場合もあります。 このような場合、ダミーの UPDATE ステートメントを明示的に追加して、変更をレプリケートする必要があります。 ダミーの UPDATE ステートメントは、レプリケーション ストアド プロシージャを使用して追加できます。  
  
### <a name="to-add-a-dummy-update-statement"></a>ダミーの UPDATE ステートメントを追加するには  
  
1.  ダミーの更新を必要とするマージ パブリッシュ済みテーブルの行に対して、操作 (たとえば UPDATETEXT など) を実行します。  
  
2.  サーバー (パブリッシャーまたはサブスクライバー) 上の変更が加えられたデータベースに対して、[sp_mergedummyupdate &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql.md) を実行します。 変更が加えられたテーブルを **@source_object**に指定し、変更された行の一意な識別子を **@rowguid**を実行します。  
  
3.  サブスクリプションを同期して、変更された行をレプリケートします。  
  
  
