---
title: sp_dbmmonitorchangealert (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitorchangealert_TSQL
- sp_dbmmonitorchangealert
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbmmonitorchangealert
- database mirroring [SQL Server], monitoring
ms.assetid: 1b29f82b-9cf8-4539-8d5c-9a1024db8a50
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2749e964b33179d5bf87ee6d464d251c14ee82d8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108145"
---
# <a name="sp_dbmmonitorchangealert-transact-sql"></a>sp_dbmmonitorchangealert (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したミラーリングのパフォーマンス基準に対する警告しきい値を追加または変更します。  

  
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dbmmonitorchangealert database_name   
    , alert_id   
    , alert_threshold   
    , enabled   
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 指定した警告しきい値を追加または変更するデータベースを指定します。  
  
 *alert_id*  
 追加または変更する警告を識別する整数値。 次のいずれかの値を指定します。  
  
|Value|パフォーマンス基準|警告しきい値|  
|-----------|------------------------|-----------------------|  
|1 で保護されたプロセスとして起動されました|最も古い未送信のトランザクション|送信キュー内にトランザクションを累積できる時間 (分単位) を指定します。この時間を経過すると、プリンシパル サーバー インスタンスで警告が生成されます。 この警告は、時間の観点からデータ損失の可能性を測定するのに役立ち、特に高パフォーマンスモードに関連しています。 パートナーとの通信が切断されたためにミラーリングが一時停止または中断している場合は、高安全モードにも関係します。|  
|2|未送信のログ|未送信のログのサイズ (KB) を指定します。このサイズを超えると、プリンシパル サーバー インスタンスで警告が生成されます。 この警告は、データ損失の可能性を KB 単位で測定するのに役立ち、特に高パフォーマンスモードに関連しています。 パートナーとの通信が切断されたためにミラーリングが一時停止または中断している場合は、高安全モードにも関係します。|  
|3|未復元のログ|未復元のログのサイズ (KB) を指定します。このサイズを超えると、ミラー サーバー インスタンスで警告が生成されます。 この警告を使用すると、フェールオーバー時間を判断できます。 *フェールオーバー時間*は、主に、以前のミラーサーバーが再実行キューに残っているログをロールフォワードするために必要な時間に加えて、短い時間が必要です。|  
|4|ミラー コミットのオーバーヘッド|許容可能な、トランザクションあたりの平均遅延時間 (ミリ秒単位) を指定します。この時間を経過すると、プリンシパル サーバーで警告が生成されます。 この遅延時間は、ミラー サーバー インスタンスによってトランザクションのログ レコードが再実行キューに書き込まれるのをプリンシパル サーバー インスタンスが待機している間、発生したオーバーヘッドの量になります。 この値は高安全モードにのみ関係します。|  
|5|保持期間|データベースミラーリング状態テーブルの行を保持する期間を制御するメタデータ。|  
  
 警告に対応するイベント Id の詳細については、「 [&#40;SQL Server&#41;](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)」を参照してください。  
  
 *alert_threshold*  
 警告のしきい値。 ミラーリングの状態が更新されたときに、このしきい値を超える値が返された場合は、Windows イベントログにエントリが入力されます。 この値は、パフォーマンスメトリックに応じて、KB、分、またはミリ秒を表します。  
  
> [!NOTE]  
>  現在の値を表示するには、 [sp_dbmmonitorresults](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)ストアドプロシージャを実行します。  
  
 *enabled*  
 警告が有効になっていますか?  
  
 0 = 警告は無効です。  
  
 1 = 警告は有効です。  
  
> [!NOTE]  
>  保有期間は常に有効になります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>アクセス許可  
 
  **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースについて、各パフォーマンス基準のしきい値と保有期間を設定します。 次の表に、この例で使用する値を示します。  
  
|*alert_id*|パフォーマンス基準|警告しきい値|警告が有効になっていますか?|  
|-----------------|------------------------|-----------------------|-----------------------------|  
|1 で保護されたプロセスとして起動されました|最も古い未送信のトランザクション|30 分|はい|  
|2|未送信のログ|1万 KB|はい|  
|3|未復元のログ|1万 KB|はい|  
|4|ミラー コミットのオーバーヘッド|1000ミリ秒|いいえ|  
|5|保持期間|8 時間|はい|  
  
```  
EXEC sp_dbmmonitorchangealert AdventureWorks2012, 1, 30, 1 ;  
EXEC sp_dbmmonitorchangealert AdventureWorks2012, 2, 10000, 1 ;  
EXEC sp_dbmmonitorchangealert AdventureWorks2012, 3, 10000, 1 ;  
EXEC sp_dbmmonitorchangealert AdventureWorks2012, 4, 1000, 0 ;  
EXEC sp_dbmmonitorchangealert AdventureWorks2012, 5, 8, 1 ;  
```  
  
## <a name="see-also"></a>参照  
 [データベースミラーリングの監視 &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorhelpalert &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpalert-transact-sql.md)   
 [sp_dbmmonitordropalert &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropalert-transact-sql.md)  
  
  
