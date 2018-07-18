---
title: レプリケーションに対して外部キー制約を無効にする方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- constraints [SQL Server], foreign keys
- foreign keys [SQL Server], disabling constraints
- disabling constraints
ms.assetid: 4211f2fd-d16a-4081-995c-43f1f0827f0b
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 11c1452224bdeef6d4a5b654bcca63a7450ddb05
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37296312"
---
# <a name="disable-foreign-key-constraints-for-replication"></a>レプリケーションに対して外部キー制約を無効にする方法
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、レプリケーションに対する外部キー制約を無効にできます。 これは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からのデータをパブリッシュする場合に便利です。  
  
> [!NOTE]  
>  レプリケーションを使用してテーブルをパブリッシュした場合、レプリケーション エージェントが実行する操作については外部キー制約が自動的に無効になります。 レプリケーション エージェントがサブスクライバー側で挿入、更新、または削除を実行した場合、制約のチェックは行われません。ユーザーが挿入、更新、または削除を実行した場合は、制約のチェックが行われます。 制約がレプリケーション エージェントに対して無効になるのは、データが最初に挿入、更新、または削除された際に、発行者側で既に制約がチェックされているためです。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **以下を使用してレプリケーションに対する外部キー制約を無効にするには**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 テーブルに対する ALTER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-disable-a-foreign-key-constraint-for-replication"></a>レプリケーションに対して外部キー制約を無効にするには  
  
1.  **オブジェクト エクスプローラー**で、変更する外部キー制約が含まれているテーブルを展開し、 **[キー]** フォルダーを展開します。  
  
2.  外部キー制約を右クリックし、 **[変更]** をクリックします。  
  
3.  **[外部キーのリレーションシップ]** ダイアログ ボックスで、 **[レプリケーションに対して適用]** の値として **[いいえ]** を選択します。  
  
4.  **[閉じる]** をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-disable-a-foreign-key-constraint-for-replication"></a>レプリケーションに対して外部キー制約を無効にするには  
  
1.  [!INCLUDE[tsql](../../includes/tsql-md.md)]でこの作業を実行するには、外部キー制約を削除します。 次に、新しい外部キー制約を追加し、NOT FOR REPLICATION オプションを指定します。  
  
 詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」を参照してください。  
  
###  <a name="TsqlExample"></a>  
