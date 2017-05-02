---
title: "データベースのターゲットの復旧時間の変更 (SQL Server) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 08/24/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e466419a-d8a4-48f7-8d97-13a903ad6b15
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6daed0f65622cd6a0533db68441021cb8c8f0a1c
ms.lasthandoff: 04/11/2017

---
# <a name="change-the-target-recovery-time-of-a-database-sql-server"></a>データベースのターゲットの復旧時間の変更 (SQL Server)
  このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の [!INCLUDE[tsql](../../includes/tsql-md.md)]データベースのターゲットの復旧時間を変更する方法について説明します。 既定では、ターゲットの復旧時間は 60 秒です。データベースで *間接チェックポイント*が使用されます。 ターゲットの復旧時間により、このデータベースの復旧時間に上限が設定されます。  
  
> [!NOTE]  
>  ターゲットの復旧時間の設定によって特定のデータベースに対して指定された上限は、実行時間の長いトランザクションによって UNDO が過度に繰り返される場合には超過することがあります。  
  
-   **Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)  
  
-   **To change the target recovery time, using:**  [SQL Server Management Studio](#SSMSProcedure) or [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項 
  
> [!CAUTION]  
>  間接チェックポイントが構成されたデータベースでオンライン トランザクション ワークロードが生じると、パフォーマンスが低下することがあります。 間接チェックポイントは、ターゲットの復旧時間内でデータベースの回復が完了するように、ダーティ ページの数が特定のしきい値を下回るようにします。 復旧間隔構成オプションは、ダーティ ページ数を使用する間接チェックポイントとは異なり、トランザクション数を使用して復旧時間を決定します。 DML 操作の受信数が多いデータベースで間接チェックポイントが有効な場合、バックグラウンド ライターは積極的にディスクにダーティ バッファーのフラッシュを開始し、回復を実行するのに必要な時間をデータベースのターゲット復旧時間内にすることができます。 これにより、ディスクのサブシステムが I/O のしきい値よりも高い動作をするかまたはその値に近づいた場合、パフォーマンス ボトルネックの原因となる追加の I/O アクティビティが特定のシステムで発生する可能性があります。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 データベースに対する ALTER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 **ターゲットの復旧時間を変更するには**  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  変更するデータベースを右クリックし、 **[プロパティ]** をクリックします。  
  
3.  **[データベースのプロパティ]** ダイアログ ボックスで、 **[オプション]** ページをクリックします。  
  
4.  **[復旧]** パネルの **[ターゲットの復旧時間 (秒)]** フィールドで、このデータベースの復旧時間の上限にする秒数を指定します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 **ターゲットの復旧時間を変更するには**  
  
1.  データベースがある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続します。  
  
2.  次の [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-set-options.md)ステートメントを、次のように使用します。  
  
     TARGET_RECOVERY_TIME **=***target_recovery_time* { SECONDS | MINUTES }  
  
     *target_recovery_time*  
     [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)]より、既定値は 1 分です。 0 (旧バージョンの既定値) より大きい値の場合は、指定されたデータベースでクラッシュが発生したときの復旧時間に上限を指定します。  
  
     SECONDS  
     *target_recovery_time* が秒単位で表されていることを示します。  
  
     MINUTES  
     *target_recovery_time* が分単位で表されていることを示します。  
  
     次の例では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースのターゲットの復旧時間を `60` 秒に設定します。  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET TARGET_RECOVERY_TIME = 60 SECONDS;  
    ```  
  
## <a name="see-also"></a>参照  
 [データベース チェックポイント &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md)   
 [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
  

