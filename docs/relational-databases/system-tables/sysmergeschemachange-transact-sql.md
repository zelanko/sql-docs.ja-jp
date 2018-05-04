---
title: sysmergeschemachange (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysmergeschemachange_TSQL
- sysmergeschemachange
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergeschemachange system table
ms.assetid: ae9ce16e-6ee9-4c7c-8210-a9bf2c7efdf0
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 526a23a19e0e2f9574f6f8b9cb316e5ecd62b0bc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysmergeschemachange-transact-sql"></a>sysmergeschemachange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  スナップショット エージェントによって生成された、パブリッシュされたアーティクルに関する情報を格納します。 このテーブルは、パブリケーション データベースとサブスクリプション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**pubid**|**uniqueidentifier**|パブリケーションの ID。|  
|**artid**|**uniqueidentifier**|アーティクルの ID。|  
|**schemaversion**|**int**|前回のスキーマ変更の番号。|  
|**される**|**uniqueidentifier**|前回のスキーマの一意な ID。|  
|**schematype**|**int**|スキーマ変更の種類。<br /><br /> **-1** = 無効。<br /><br /> **1** SQL コマンドを = です。<br /><br /> **2**スキーマ スクリプトを = です。<br /><br /> **3**ネイティブの一括コピー プログラム ユーティリティ (BCP) を = です。<br /><br /> **4** = キャラクター BCP。<br /><br /> **5** = 前回記録された生成結果。<br /><br /> **6** = 前回送信された生成結果。<br /><br /> **7**ディレクトリを = です。<br /><br /> **8**優先度を = です。<br /><br /> **9**保有期間を = です。<br /><br /> **10** = トリガー スクリプト。<br /><br /> **11** Alter table を = です。<br /><br /> **12** = すべて再初期化します。<br /><br /> **13** = ALTER TABLE (非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])。<br /><br /> **14**アップロードと共に再初期化を = です。<br /><br /> **15**制約とインデックスのスクリプトを = です。<br /><br /> **16**メタデータのクリーンアップを = です。<br /><br /> **17** = 前回送信された生成結果を更新します。<br /><br /> **18**旧バージョンとの互換性レベルを = です。<br /><br /> **19**サブスクライバー情報の検証を = です。<br /><br /> **20** = 完全なパーティション分割します。<br /><br /> **21**カスタム競合回避モジュールを = です。<br /><br /> **22**アーティクルの処理順序を = です。<br /><br /> **23**トランザクション パブリケーションの発行を = です。<br /><br /> **24**エラーの補正を = です。<br /><br /> **25**代替スナップショット フォルダーを = です。<br /><br /> **26** = ダウンロードのみです。<br /><br /> **27**削除の追跡を = です。<br /><br /> **40**スナップショットの事前作成スクリプトを = です。<br /><br /> **45** = 事後作成のスナップショット スクリプトです。<br /><br /> **46**の要求時ユーザー スクリプトを = です。<br /><br /> **50** = スナップショット ヘッダー開始します。<br /><br /> **51** = スナップショット ヘッダー終了します。<br /><br /> **52**スナップショット トレーラーを = です。<br /><br /> **53**ファイル転送プロトコル (FTP) アドレスを = です。<br /><br /> **54** FTP ポートを = です。<br /><br /> **55** = FTP サブディレクトリです。<br /><br /> **56**圧縮スナップショットを = です。<br /><br /> **57** FTP のログインを = です。<br /><br /> **58** FTP のパスワードを = です。<br /><br /> **60**システムの事前作成スクリプトを = です。<br /><br /> **61**ストアド プロシージャ スキーマを = です。<br /><br /> **62**ビューのスキーマを = です。<br /><br /> **63**ユーザー定義関数のスキーマを = です。<br /><br /> **64**ビューのインデックスを = です。<br /><br /> **65**拡張プロパティを = です。<br /><br /> **66** = 検証します。<br /><br /> **67** = プリスナップ ショット SQL コマンド。<br /><br /> **71**動的スナップショット検証を = です。<br /><br /> **80** = システム テーブル ネイティブ BCP 9.0 です。<br /><br /> **81**システム テーブル キャラクター BCP 9.0 を = です。<br /><br /> **82** = システム テーブル ネイティブ BCP 9.0 (グローバルのみ)。<br /><br /> **83** = システム テーブル キャラクター BCP 9.0 (グローバルのみ)。<br /><br /> **84** = システム テーブル ネイティブ BCP 9.0 (簡易)。<br /><br /> **85** = システム テーブル キャラクター BCP 9.0 (簡易)。<br /><br /> **128** = 動的 BCP (bit)。<br /><br /> **131** = 動的ネイティブ BCP。<br /><br /> **132** = 動的キャラクター BCP。<br /><br /> **208** = 動的システム テーブル ネイティブ BCP 9.0 です。<br /><br /> **209** = 動的システム テーブル キャラクター BCP 9.0 です。<br /><br /> **210** = 動的システム テーブル ネイティブ BCP 9.0 (グローバルのみ)。<br /><br /> **211** = 動的システム テーブル キャラクター BCP 9.0 (グローバルのみ)。<br /><br /> **212** = 動的システム テーブル ネイティブ BCP 9.0 (簡易)。<br /><br /> **213** = 動的システム テーブル キャラクター BCP 9.0 (簡易)。<br /><br /> **300**データ定義言語 (DDL) 操作を = です。<br /><br /> **1024** = 増分スナップショット コントロール。<br /><br /> **1049** = 増分スナップショット フォルダーです。<br /><br /> **1074** = 増分スナップショット ヘッダー開始します。<br /><br /> **1075** = 増分スナップショット ヘッダー終了します。<br /><br /> **1076**増分スナップショット トレーラーを = です。<br /><br /> **1077** = 増分 FTP アドレス。<br /><br /> **1078** = 増分 FTP ポートです。<br /><br /> **1079** = 増分 FTP サブディレクトリです。<br /><br /> **1080**増分圧縮されたスナップショットを = です。<br /><br /> **1081** = 増分 FTP ログインします。<br /><br /> **1082** = 増分 FTP パスワードです。|  
|**schematext**|**nvarchar(2000)**|スクリプト ファイルの名前、またはファイル名を含むコマンド。|  
|**schemastatus**|**tinyint**|スキーマの変更が保留中かどうかを示す、アーティクルのこともある、次の値のいずれか。<br /><br /> **0** = 非アクティブです。<br /><br /> **1**アクティブを = です。<br /><br /> この値が に設定されているスキーマの変更が保留中の場合は、 **1**です。|  
|**schemasubtype**|**int**|スキーマ変更のサブタイプ。<br /><br /> **1** ADDCOLUMN を =<br /><br /> **2** DROPCOLUMN を =<br /><br /> **3** ALTERCOLUMN を =<br /><br /> **4** ADDPRIMARYKEY を =<br /><br /> **5** ADDUNIQUE を =<br /><br /> **6** ADDREFERENCE を =<br /><br /> **7** DROPCONSTRAINT を =<br /><br /> **8** ADDDEFAULT を =<br /><br /> **9** ADDCHECK を =<br /><br /> **10** DISABLETRIGGER<br /><br /> **11** ENABLETRIGGER<br /><br /> **12** DISABLETRIGGER<br /><br /> **13** ENABLETRIGGER<br /><br /> **14** ENABLECONSTRAINT<br /><br /> **15** DISABLECONSTRAINT<br /><br /> **16** ENABLECONSTRAINT<br /><br /> **17** DISABLECONSTRAINT|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
