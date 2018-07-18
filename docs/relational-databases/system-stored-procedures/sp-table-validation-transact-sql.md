---
title: sp_table_validation (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_table_validation_TSQL
- sp_table_validation
helpviewer_keywords:
- sp_table_validation
ms.assetid: 31b25f9b-9b62-496e-a97e-441d5fd6e767
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: d82517f09ad18c7cc0b2e8d49acfdae6ab200ee9
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38037020"
---
# <a name="sptablevalidation-transact-sql"></a>sp_table_validation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  テーブルまたはインデックス付きビューの行数またはチェックサム情報を返すか、あるいは提供された行数またはチェックサム情報を指定のテーブルまたはインデックス付きビューと比較します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて、およびサブスクライバー側でサブスクリプション データベースについて実行されます。 *Oracle パブリッシャーに対してはサポートされていません*します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_table_validation [ @table = ] 'table'  
    [ , [ @expected_rowcount = ] type_of_check_requested OUTPUT]  
    [ , [ @expected_checksum = ] expected_checksum OUTPUT]  
    [ , [ @rowcount_only = ] rowcount_only ]  
    [ , [ @owner = ] 'owner' ]  
    [ , [ @full_or_fast = ] full_or_fast ]  
    [ , [ @shutdown_agent = ] shutdown_agent ]  
    [ , [ @table_name = ] table_name ]  
    [ , [ @column_list = ] 'column_list' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@table=**] **'***テーブル***'**  
 テーブルの名前を指定します。 *テーブル*は**sysname**、既定値はありません。  
  
 [  **@expected_rowcount=**] *expected_rowcount*出力  
 テーブル内の予想される行数を返すかどうかを指定します。 *expected_rowcount*は**int**、既定値は NULL です。 NULL の場合、実際の行数が出力パラメーターとして返されます。 値が提供されると、その値は実際の行数と照合され、違いがあるかどうかが識別されます。  
  
 [  **@expected_checksum=**] *expected_checksum*出力  
 テーブルの予想されるチェックサムを返すかどうかを指定します。 *expected_checksum*は**数値**、既定値は NULL です。 NULL の場合、実際のチェックサムが出力パラメーターとして返されます。 値が提供されると、その値は実際のチェックサムと照合され、違いがあるかどうかが識別されます。  
  
 [  **@rowcount_only=**] *type_of_check_requested*  
 実行するチェックサムまたは行数の種類を指定します。 *type_of_check_requested*は**smallint**、既定値は**1**します。  
  
 場合**0**、行数を実行し、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 互換のチェックサム。  
  
 場合**1**、行数チェックのみを実行します。  
  
 場合**2**行数とバイナリ チェックサムを実行します。  
  
 [  **@owner=**] **'***所有者***'**  
 テーブルの所有者の名前を指定します。 *所有者*は**sysname**、既定値は NULL です。  
  
 [  **@full_or_fast=**] *full_or_fast*  
 行数の計算で使用する方法を指定します。 *full_or_fast*は**tinyint**、既定値は**2**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|COUNT(*) を使用してフル カウントします。|  
|**1**|高速カウントから**sysindexes.rows**します。 行のカウント**sysindexes**実際のテーブル内の行のカウントより高速です。 ただし、ため**sysindexes**が遅れて更新されると、行カウントが不正確になります。|  
|**2** (既定値)|最初に高速カウントを試み、条件高速カウントを行います。 高速カウントに違いが見られる場合、フル カウントに戻されます。 場合*expected_rowcount*ストアド プロシージャの中を NULL 値を取得する、フル カウント(\*) が常に使用します。|  
  
 [  **@shutdown_agent=**] *shutdown_agent*  
 ディストリビューション エージェントが実行している場合**sp_table_validation**検証の完了後、ディストリビューション エージェント、直ちにシャットかどうかを指定します。 *shutdown_agent*は**ビット**、既定値は**0**します。 場合**0**、レプリケーション エージェントがシャット ダウンされません。 場合**1**レプリケーション エージェントがシャット ダウンにシグナル状態、エラー 20578 が発生します。 このパラメーターは無視されますと**sp_table_validation**ユーザーが直接実行されます。  
  
 [  **@table_name =**] *table_name*  
 出力メッセージ用に使用されるビューのテーブル名です。 *table_name*は**sysname**、既定値は **@table**します。  
  
 [ **@column_list**=] **'***column_list***'**  
 チェックサム関数で使用する列リストです。 *column_list*は**nvarchar (4000)**、既定値は NULL です。 マージ アーティクルを検証する場合は、計算列とタイムスタンプ列を除く列リストを指定します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 表に、チェックサム、チェックサムの検証と予想されるチェックサムを実行すると等しい場合**sp_table_validation**テーブルがチェックサムの検証を渡すことのメッセージが返されます。 一致しない場合は、テーブルの同期がとられていない可能性があるというメッセージを返し、予想される行数と実際の行数の違いをレポートします。  
  
 テーブルの数、行数検証と予期された行数を実行すると等しい場合**sp_table_validation**テーブルが行数の検証を渡すことのメッセージが返されます。 一致しない場合は、テーブルの同期がとられていない可能性があるというメッセージを返し、予想される行数と実際の行数の違いをレポートします。  
  
## <a name="remarks"></a>コメント  
 **sp_table_validation**はあらゆる種類のレプリケーションで使用します。 **sp_table_validation**は Oracle パブリッシャーに対してはサポートされていません。  
  
 チェックサムは、ページ上の行イメージ全体で 32 ビット巡回冗長検査 (CRC) を計算します。 チェックサムは、列を選択して検査するわけではなく、テーブルのビューや列方向のパーティションで動作できません。 また、チェックサムの内容をスキップします。**テキスト**と**イメージ**(デザイン) によって列。  
  
 チェックサムを実行する場合、2 つのサーバー間でテーブルの構造が一致している必要があります。つまり、テーブルの列はその順序、データ型、長さ、NULL/NOT NULL 条件がすべて同じでなければなりません。 たとえば、パブリッシャーが CREATE TABLE を実行し、ALTER TABLE で列を追加している場合、サブスクライバーで適用されたスクリプトが CREATE TABLE だけであれば、構造は同じではありません。 2 つのテーブルの構造が同じであることを特定でない場合を見て[syscolumns](../../relational-databases/system-compatibility-views/sys-syscolumns-transact-sql.md)各テーブル内のオフセットが同じであることを確認します。  
  
 浮動小数点値はキャラクター モードの場合は、チェックサムの違いを生成する可能性が**bcp**を使用した場合、パブリケーションに含まれていない場合は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバー。 これは、文字モード間で変換を実行するときの、わずかではあるが避けられない有効桁数の違いに基づきます。  
  
## <a name="permissions"></a>アクセス許可  
 実行する**sp_table_validation**、検証対象のテーブルに対する SELECT 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [チェックサム&#40;TRANSACT-SQL&#41;](../../t-sql/functions/checksum-transact-sql.md)   
 [@@ROWCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/rowcount-transact-sql.md)   
 [sp_article_validation &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md)   
 [sp_publication_validation &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
