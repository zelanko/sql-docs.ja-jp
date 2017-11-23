---
title: "OBJECTPROPERTYEX (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OBJECTPROPERTYEX
- OBJECTPROPERTYEX_TSQL
dev_langs: TSQL
helpviewer_keywords:
- displaying schema-scoped object information
- viewing schema-scoped object information
- OBJECTPROPERTYEX function
- schema-scoped objects [SQL Server]
- objects [SQL Server], schema-scoped
ms.assetid: be36b3e3-3309-4332-bfb5-c7e9cf8dc8bd
caps.latest.revision: "76"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 63854d22cf1285fee6758ee0e78da0c13bb21dc6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="objectpropertyex-transact-sql"></a>OBJECTPROPERTYEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベース内のスキーマ スコープ オブジェクトに関する情報を返します。 これらのオブジェクトの一覧は、次を参照してください。 [sys.objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md). OBJECTPROPERTYEX は、データ定義言語 (DDL) トリガーやイベント通知などの非スキーマ スコープ オブジェクトには使用できません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
OBJECTPROPERTYEX ( id , property )  
```  
  
## <a name="arguments"></a>引数  
 *id*  
 現在のデータベース内のオブジェクトの ID を表す式を指定します。 *id*は**int**は現在のデータベース コンテキストでのスキーマ スコープ オブジェクトであると仮定します。  
  
 *プロパティ*  
 ID で指定したオブジェクトについて、返される情報を含む式を指定します。戻り値の型は**sql_variant**です。 次の表は、各プロパティ値に対する基本のデータ型です。  
  
> [!NOTE]  
>  明記しない限り、NULL が返されます*プロパティ*有効なプロパティ名ではない*id* 、有効なオブジェクト ID ではありません*id*は、指定された、サポートされていないオブジェクト型です。*プロパティ*、か、呼び出し元に、オブジェクトのメタデータを表示するアクセス許可がありません。  
  
|プロパティ名|オブジェクトの種類|説明と戻り値|  
|-------------------|-----------------|-------------------------------------|  
|BaseType|任意のスキーマ スコープ オブジェクト|オブジェクトの基本の種類。 指定したオブジェクトが SYNONYM の場合、基になるオブジェクトの基本の種類が返されます。<br /><br /> NULL 以外 = オブジェクトの種類<br /><br /> 基本データ型: **char(2)**|  
|CnstIsClustKey|制約|クラスター化インデックスを指定した PRIMARY KEY 制約。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|CnstIsColumn|制約|単一の列での、CHECK、DEFAULT、または FOREIGN KEY 制約。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|CnstIsDeleteCascade|制約|ON DELETE CASCADE オプションを指定した FOREIGN KEY 制約。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|CnstIsDisabled|制約|制約の無効化。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|CnstIsNonclustKey|制約|非クラスター化インデックスを指定した PRIMARY KEY 制約。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|CnstIsNotRepl|制約|制約を NOT FOR REPLICATION キーワードを使って定義。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|CnstIsNotTrusted|制約|既存の行を確認せずに制約が有効化されており、 すべての行に制約が保持されない可能性があります。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|CnstIsUpdateCascade|制約|ON UPDATE CASCADE オプションを指定した FOREIGN KEY 制約。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|ExecIsAfterTrigger|トリガー|AFTER トリガー。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|ExecIsAnsiNullsOn|[!INCLUDE[tsql](../../includes/tsql-md.md)]関数、[!INCLUDE[tsql](../../includes/tsql-md.md)]プロシージャ[!INCLUDE[tsql](../../includes/tsql-md.md)]トリガー、ビュー|作成時に ANSI_NULLS の設定です。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|ExecIsDeleteTrigger|トリガー|DELETE トリガー。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|ExecIsFirstDeleteTrigger|トリガー|テーブルに対して DELETE を実行するときに最初に起動されるトリガー。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|ExecIsFirstInsertTrigger|トリガー|テーブルに対して INSERT を実行するときに最初に起動されるトリガー。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|ExecIsFirstUpdateTrigger|トリガー|テーブルに対して UPDATE を実行するときに最初に起動されるトリガー。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|ExecIsInsertTrigger|トリガー|INSERT トリガー。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|ExecIsInsteadOfTrigger|トリガー|INSTEAD OF トリガー。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|ExecIsLastDeleteTrigger|トリガー|テーブルに対して DELETE を実行するときに最後に起動されるトリガー。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|ExecIsLastInsertTrigger|トリガー|テーブルに対して INSERT を実行するときに最後に起動されるトリガー。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|ExecIsLastUpdateTrigger|トリガー|テーブルに対して UPDATE を実行するときに最後に起動されるトリガー。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|ExecIsQuotedIdentOn|[!INCLUDE[tsql](../../includes/tsql-md.md)]関数、[!INCLUDE[tsql](../../includes/tsql-md.md)]プロシージャ[!INCLUDE[tsql](../../includes/tsql-md.md)]トリガー、ビュー|作成時における QUOTED_IDENTIFIER の設定。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|ExecIsStartup|手順|スタートアップ プロシージャ。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|ExecIsTriggerDisabled|トリガー|トリガーの無効化。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|ExecIsTriggerNotForRepl|トリガー|NOT FOR REPLICATION として定義されているトリガー。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|ExecIsUpdateTrigger|トリガー|UPDATE トリガー。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|ExecIsWithNativeCompilation|[!INCLUDE[tsql](../../includes/tsql-md.md)] プロシージャ|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> プロシージャはネイティブでコンパイルされます。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|HasAfterTrigger|テーブル、ビュー|テーブルまたはビューに AFTER トリガーがあります。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|HasDeleteTrigger|テーブル、ビュー|テーブルまたはビューに DELETE トリガーがあります。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|HasInsertTrigger|テーブル、ビュー|テーブルまたはビューに INSERT トリガーがあります。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|HasInsteadOfTrigger|テーブル、ビュー|テーブルまたはビューに INSTEAD OF トリガーがあります。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|HasUpdateTrigger|テーブル、ビュー|テーブルまたはビューに UPDATE トリガーがあります。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsAnsiNullsOn|[!INCLUDE[tsql](../../includes/tsql-md.md)]関数、[!INCLUDE[tsql](../../includes/tsql-md.md)]プロシージャ、テーブル、[!INCLUDE[tsql](../../includes/tsql-md.md)]トリガー、ビュー|テーブルに対する ANSI NULLS オプションの設定をオンに指定します。NULL 値に対するすべての比較は UNKNOWN として評価されます。 この設定は、テーブルが存在する限り、計算列や制約をはじめとするテーブル定義内のすべての式に適用されます。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsCheckCnst|任意のスキーマ スコープ オブジェクト|CHECK 制約。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsConstraint|任意のスキーマ スコープ オブジェクト|制約。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsDefault|任意のスキーマ スコープ オブジェクト|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 既定のバインド。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsDefaultCnst|任意のスキーマ スコープ オブジェクト|DEFAULT 制約。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsDeterministic|スカラーおよびテーブル値関数、ビュー|関数またはビューの決定性を示すプロパティ。<br /><br /> 1 = 決定的<br /><br /> 0 = 非決定的<br /><br /> 基本データ型: **int**|  
|IsEncrypted|[!INCLUDE[tsql](../../includes/tsql-md.md)]関数、[!INCLUDE[tsql](../../includes/tsql-md.md)]プロシージャ、テーブル、[!INCLUDE[tsql](../../includes/tsql-md.md)]トリガー、ビュー|モジュール ステートメントの元のテキストが、暗号化した形式に変換されたことを示します。 難読化の出力内のカタログ ビューのいずれかで直接表示がない[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]です。 システム テーブルまたはデータベース ファイルにアクセスすることがなくユーザーには、難読化されたテキストを取得できません。 ただし、テキストは経由でシステム テーブルにアクセスするか、ユーザーが使用できる、 [DAC ポート](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)または直接データベース ファイルにアクセスします。 また、サーバー プロセスにデバッガーをアタッチできるユーザーは、実行時、元のプロシージャをメモリから取得できます。<br /><br /> 1 = 暗号化<br /><br /> 0 = 暗号化されていません。<br /><br /> 基本データ型: **int**|  
|IsExecuted|任意のスキーマ スコープ オブジェクト|オブジェクトは実行可能 (ビュー、プロシージャ、関数、またはトリガー)。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsExtendedProc|任意のスキーマ スコープ オブジェクト|拡張プロシージャ。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsForeignKey|任意のスキーマ スコープ オブジェクト|FOREIGN KEY 制約。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsIndexed|テーブル、ビュー|テーブルまたはインデックス付きのビュー。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsIndexable|テーブル、ビュー|テーブルまたはビューのインデックスが作成されます。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsInlineFunction|関数|インライン関数。<br /><br /> 1 = インライン関数<br /><br /> 0 = インライン関数ではない<br /><br /> 基本データ型: **int**|  
|IsMSShipped|任意のスキーマ スコープ オブジェクト|インストール中に作成されたオブジェクト[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsPrecise|計算列、関数、ユーザー定義型、ビュー|浮動小数点演算など、不正確な計算を含むオブジェクトかどうかを示します。<br /><br /> 1 = 正確<br /><br /> 0 = 不正確<br /><br /> 基本データ型: **int**|  
|IsPrimaryKey|任意のスキーマ スコープ オブジェクト|PRIMARY KEY 制約。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsProcedure|任意のスキーマ スコープ オブジェクト|プロシージャ。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsQuotedIdentOn|CHECK 制約、DEFAULT 定義、[!INCLUDE[tsql](../../includes/tsql-md.md)]関数、[!INCLUDE[tsql](../../includes/tsql-md.md)]プロシージャ、テーブル、[!INCLUDE[tsql](../../includes/tsql-md.md)]トリガー、ビュー|オブジェクトの引用符で囲まれた識別子の設定をオンに指定します。オブジェクト定義に含まれるすべての式の識別子は、二重引用符によって区切られます。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsQueue|任意のスキーマ スコープ オブジェクト|Service Broker キュー。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsReplProc|任意のスキーマ スコープ オブジェクト|レプリケーション プロシージャ。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsRule|任意のスキーマ スコープ オブジェクト|ルールのバインド。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsScalarFunction|関数|スカラー値関数。<br /><br /> 1 = スカラー値関数<br /><br /> 0 = スカラー値関数ではない<br /><br /> 基本データ型: **int**|  
|IsSchemaBound|関数、プロシージャ、ビュー|SCHEMABINDING を使用して作成されたスキーマ バインド関数またはビュー。<br /><br /> 1 = スキーマ バインド<br /><br /> 0 = 非スキーマ バインド<br /><br /> 基本データ型: **int**|  
|IsSystemTable|テーブル|システム テーブル。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsSystemVerified|計算列、関数、ユーザー定義型、ビュー|オブジェクトの精度と決定性のプロパティを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で確認できます。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsTable|テーブル|テーブル。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsTableFunction|関数|テーブル値関数。<br /><br /> 1 = テーブル値関数<br /><br /> 0 = テーブル値関数ではない<br /><br /> 基本データ型: **int**|  
|IsTrigger|任意のスキーマ スコープ オブジェクト|トリガーです。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsUniqueCnst|任意のスキーマ スコープ オブジェクト|UNIQUE 制約。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsUserTable|テーブル|ユーザー定義テーブル。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|IsView|表示|ビュー。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|OwnerId|任意のスキーマ スコープ オブジェクト|オブジェクトの所有者です。<br /><br /> **注:**必ずしもオブジェクト所有者がスキーマの所有者ではありません。 たとえば、子オブジェクト (いる*parent_object_id*が null でない) は常に、親と同じ所有者の ID を返します。<br /><br /> NULL 以外 = オブジェクト所有者のデータベース ユーザー ID<br /><br /> NULL = サポートされていないオブジェクトの種類、またはオブジェクト ID が有効でない<br /><br /> 基本データ型: **int**|  
|SchemaId|任意のスキーマ スコープ オブジェクト|オブジェクトに関連付けられているスキーマの ID。<br /><br /> NULL 以外 = オブジェクトのスキーマ ID<br /><br /> 基本データ型: **int**|  
|SystemDataAccess|関数、ビュー|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンス内にある、システム データ、システム カタログ、または仮想システム テーブルにオブジェクトがアクセスします。<br /><br /> 0 = なし<br /><br /> 1 = 読み取り<br /><br /> 基本データ型: **int**|  
|TableDeleteTrigger|テーブル|テーブルに DELETE トリガーがあります。<br /><br /> >1 = 指定された種類の最初のトリガーの ID<br /><br /> 基本データ型: **int**|  
|TableDeleteTriggerCount|テーブル|テーブルに、指定された数の DELETE トリガーがあります。<br /><br /> NULL 以外 = DELETE トリガーの数<br /><br /> 基本データ型: **int**|  
|TableFullTextMergeStatus|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 現在マージ中のフルテキスト インデックスがテーブルにあるかどうかを示します。<br /><br /> 0 = テーブルにフルテキスト インデックスがないか、フルテキスト インデックスがマージ中ではない<br /><br /> 1 = フルテキスト インデックスがマージ中|  
|TableFullTextBackgroundUpdateIndexOn|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> テーブルでは、フルテキスト インデックスのバックグラウンド更新 (自動変更の追跡) が有効になっています。<br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> 基本データ型: **int**|  
|TableFulltextCatalogId|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> テーブルのフルテキスト インデックス データが存在する、フルテキスト カタログの ID。<br /><br /> 0 以外 = フルテキスト インデックス テーブル内の行を識別する一意なインデックスに関連付けられた、フルテキスト カタログ ID。<br /><br /> 0 = テーブルにフルテキスト インデックスはない。<br /><br /> 基本データ型: **int**|  
|TableFullTextChangeTrackingOn|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> テーブルでは、フルテキストの変更の追跡が有効になっています。<br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> 基本データ型: **int**|  
|TableFulltextDocsProcessed|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> フルテキスト インデックス作成の開始以降に処理された行の数。 フルテキスト検索用にインデックスが作成されるテーブルでは、1 行のすべての列が、インデックスが作成される 1 つのドキュメントの一部と見なされます。<br /><br /> 0 = アクティブ クロールまたはフルテキスト インデックス作成は完了していない<br /><br /> > 0 = 次のいずれか (A または B): A) で挿入または更新操作が開始されてからの完全、増分、または手動の変更を追跡します処理されたドキュメントの数。B) 挿入または更新操作の変更の追跡をバック グラウンド更新インデックス作成が有効になっているため、フルテキスト インデックス スキーマの変更、フルテキスト カタログの再構築すると、またはのインスタンスによって処理された行の数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]再起動とにします。<br /><br /> NULL = テーブルにフルテキスト インデックスはない。<br /><br /> 基本データ型: **int**<br /><br /> **注**このプロパティを監視または削除された行をカウントしません。|  
|TableFulltextFailCount|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> フルテキスト検索でインデックスが作成されなかった行の数。<br /><br /> 0 = 作成完了<br /><br /> > 0 = 次のいずれか (A または B): A) Full、Incremental、および手動更新の変更が追跡; が開始されてからインデックスが作成されなかったドキュメントの数B) の変更の追跡を背景には、インデックス、インデックスを作成の開始または母集団の再起動以降インデックスが作成されなかった行の数を更新します。 これは、スキーマ変更、カタログの再構築、サーバーの再起動などにより発生する場合があります。<br /><br /> NULL = テーブルにフルテキスト インデックスはない<br /><br /> 基本データ型: **int**|  
|TableFulltextItemCount|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> NULL 以外 = フルテキスト インデックスが正常に作成された行の数。<br /><br /> NULL = テーブルにフルテキスト インデックスはない。<br /><br /> 基本データ型: **int**|  
|TableFulltextKeyColumn|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> フルテキスト インデックスとセマンティック インデックスの定義の一部である、一意な単一列インデックスに関連付けられた列の ID。<br /><br /> 0 = テーブルにフルテキスト インデックスはない。<br /><br /> 基本データ型: **int**|  
|TableFulltextPendingChanges|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 変更の追跡が処理されていないエントリ数。<br /><br /> 0 = 変更の追跡は有効でない<br /><br /> NULL = テーブルにフルテキスト インデックスはない。<br /><br /> 基本データ型: **int**|  
|TableFulltextPopulateStatus|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 0 = アイドル状態<br /><br /> 1 = 全体を作成中<br /><br /> 2 = 増分作成中<br /><br /> 3 = 追跡した変更を伝達中<br /><br /> 4 = バック グラウンド更新インデックスは、自動変更の追跡などの進行中です。<br /><br /> 5 = フルテキスト インデックス作成が絞り込みまたは停止された<br /><br /> 6 = エラーが発生しました。 詳細については、クロール ログを確認します。 詳細については、次を参照してください。、**フルテキスト作成 (クロール) でのエラーのトラブルシューティング**のセクション[、フルテキスト インデックスの作成](../../relational-databases/search/populate-full-text-indexes.md)です。<br /><br /> 基本データ型: **int**|  
|TableFullTextSemanticExtraction|テーブル|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> テーブルでセマンティック インデックス作成が有効になっています。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableHasActiveFulltextIndex|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> テーブルにアクティブなフルテキスト インデックスがあります。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableHasCheckCnst|テーブル|テーブルに CHECK 制約があります。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableHasClustIndex|テーブル|テーブルにクラスター化インデックスがあります。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableHasDefaultCnst|テーブル|テーブルに DEFAULT 制約があります。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableHasDeleteTrigger|テーブル|テーブルに DELETE トリガーがあります。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableHasForeignKey|テーブル|テーブルに FOREIGN KEY 制約があります。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableHasForeignRef|テーブル|テーブルは FOREIGN KEY 制約により参照されています。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableHasIdentity|テーブル|テーブルに ID 列があります。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableHasIndex|テーブル|テーブルに任意の種類のインデックスがあります。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableHasInsertTrigger|テーブル|オブジェクトに INSERT トリガーがあります。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableHasNonclustIndex|テーブル|テーブルに非クラスター化インデックスがあります。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableHasPrimaryKey|テーブル|テーブルに主キーがあります。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableHasRowGuidCol|テーブル|テーブルの ROWGUIDCOL には、 **uniqueidentifier**列です。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableHasTextImage|テーブル|テーブルには、**テキスト**、 **ntext**、または**イメージ**列です。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableHasTimestamp|テーブル|テーブルには、**タイムスタンプ**列です。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableHasUniqueCnst|テーブル|テーブルに UNIQUE 制約があります。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableHasUpdateTrigger|テーブル|オブジェクトに UPDATE トリガーがあります。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableHasVarDecimalStorageFormat|テーブル|テーブルが有効になって**vardecimal**ストレージ形式です。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableInsertTrigger|テーブル|テーブルに INSERT トリガーがあります。<br /><br /> >1 = 指定された種類の最初のトリガーの ID<br /><br /> 基本データ型: **int**|  
|TableInsertTriggerCount|テーブル|テーブルに、指定された数の INSERT トリガーがあります。<br /><br /> >0 = INSERT トリガーの数<br /><br /> 基本データ型: **int**|  
|TableIsFake|テーブル|テーブルは実在せず、 オンデマンドで内部的に具体化されて、[!INCLUDE[ssDE](../../includes/ssde-md.md)]です。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableIsLockedOnBulkLoad|テーブル|テーブルがロックされているため、 **bcp**または BULK INSERT ジョブです。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|TableIsMemoryOptimized|テーブル|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> テーブルはメモリ最適化されています<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**<br /><br /> 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。|  
|TableIsPinned|テーブル|テーブルは固定され、データ キャッシュに確保されています。<br /><br /> 0 = False<br /><br /> この機能はサポートされていません[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降のバージョン。|  
|TableTextInRowLimit|テーブル|テーブルに text in row オプション セットがあります。<br /><br /> > 0 = text in row に許可されている最大バイト数。<br /><br /> 0 = テキスト行のオプションが設定されていません。<br /><br /> 基本データ型: **int**|  
|TableUpdateTrigger|テーブル|テーブルに UPDATE トリガーがあります。<br /><br /> > 1 = 指定された種類の最初のトリガーの ID<br /><br /> 基本データ型: **int**|  
|TableUpdateTriggerCount|テーブル|テーブルに、指定された数の UPDATE トリガーがあります。<br /><br /> > 0 = UPDATE トリガーの数<br /><br /> 基本データ型: **int**|  
|UserDataAccess|関数、ビュー|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンス内にある、ユーザー データやユーザー テーブルにオブジェクトがアクセスします。<br /><br /> 1 = 読み取り<br /><br /> 0 = なし<br /><br /> 基本データ型: **int**|  
|TableHasColumnSet|テーブル|テーブルに列セットがあります。<br /><br /> 0 = False<br /><br /> 1 = True<br /><br /> 詳細については、「 [列セットの使用](../../relational-databases/tables/use-column-sets.md)」を参照してください。|  
|Cardinality|テーブル (システムまたはユーザー定義)、ビュー、またはインデックス|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 指定されたオブジェクト内の行数。|  
|TableTemporalType|テーブル|**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> テーブルの種類を指定します。<br /><br /> 0 = 非一時的なテーブル<br /><br /> 1 = システムのバージョン情報のテーブルの履歴テーブル<br /><br /> 2 = システムのバージョン情報の一時的なテーブル|  
  
## <a name="return-types"></a>戻り値の型  
 **sql_variant**  
  
## <a name="exceptions"></a>例外  
 エラーが発生した場合、または呼び出し元にオブジェクトの表示権限がない場合は、NULL が返されます。  
  
 ユーザーが所有しているか、または権限を与えられている、セキュリティ保護可能なリソースのメタデータのみを表示できます。 つまり、オブジェクトに対する権限がユーザーに与えられていない場合、メタデータを生成する組み込み関数 (OBJECTPROPERTYEX など) が NULL を返す可能性があります。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]であると推定*object_id*が現在のデータベース コンテキスト。 参照するクエリ、 *object_id*別のデータベースで NULL または不適切な結果が返されます。 たとえば、次のクエリでは現在のデータベース コンテキストは、マスター データベースです。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]を指定されたプロパティの値を返そう*object_id*クエリで指定されているデータベースではなく、そのデータベースにします。 クエリが正しくない結果を返しますビュー `vEmployee` master データベースに含まれない。  
  
```  
USE master;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID(N'AdventureWorks2012.HumanResources.vEmployee'), 'IsView');  
GO  
```  
  
 OBJECTPROPERTYEX (*view_i*d, 'IsIndexable') IsIndexable プロパティの評価は、ビュー定義、正規化、および部分最適化の解析が必要なために、多くのコンピューター リソースを使用することがあります。 IsIndexable プロパティではインデックスを作成できるテーブルまたはビューを指定しますが、特定のインデックス キーの要件が満たされない場合、インデックスの実際の作成は失敗します。 詳細については、「[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)」を参照してください。  
  
 OBJECTPROPERTYEX (*table_id*、'TableHasActiveFulltextIndex') はインデックス作成のため、テーブルの少なくとも 1 つの列が追加されたときに 1 (true) の値を返します。 インデックス作成で先頭の列が追加されるとすぐ、フルテキスト インデックス作成が自動的にアクティブになります。  
  
 メタデータの表示に関する制限は、結果セットに適用されます。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-finding-the-base-type-of-an-object"></a>A. オブジェクトの基本の種類を検索する  
 次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース内の `MyEmployeeTable` テーブルに対して SYNONYM `Employee` を作成した後、SYNONYM の基本の種類を返します。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE SYNONYM MyEmployeeTable FOR HumanResources.Employee;  
GO  
SELECT OBJECTPROPERTYEX ( object_id(N'MyEmployeeTable'), N'BaseType')AS [Base Type];  
GO  
```  
  
 結果セットでは、基になるオブジェクトである `Employee` テーブルの基本の種類が、ユーザー テーブルであることが示されます。  
  
 ```
Base Type 
--------  
U
```  
  
### <a name="b-returning-a-property-value"></a>B. プロパティ値を返す  
 次の例では、指定されたテーブルの UPDATE トリガー数を返します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID(N'HumanResources.Employee'), N'TABLEUPDATETRIGGERCOUNT');  
GO  
  
```  
  
### <a name="c-finding-tables-that-have-a-foreign-key-constraint"></a>C. FOREIGN KEY 制約を含むテーブルを探す  
 次の例では、 `TableHasForeignKey` FOREIGN KEY 制約があるすべてのテーブルを取得するプロパティです。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT name, object_id, schema_id, type_desc  
FROM sys.objects   
WHERE OBJECTPROPERTYEX(object_id, N'TableHasForeignKey') = 1  
ORDER BY name;  
GO  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-finding-the-base-type-of-an-object"></a>D: オブジェクトの基本型を検索します。  
 次の例は、の基本型を返します`dbo.DimReseller`オブジェクト。  
  
```  
-- Uses AdventureWorks  
  
SELECT OBJECTPROPERTYEX ( object_id(N'dbo.DimReseller'), N'BaseType')AS BaseType;  
```  
  
 結果セットでは、基になるオブジェクトである `dbo.DimReseller` テーブルの基本の種類が、ユーザー テーブルであることが示されます。  
  
```  
BaseType   
--------   
U   
```  
  
## <a name="see-also"></a>参照  
 [シノニム &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-synonym-transact-sql.md)   
 [メタデータ関数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)   
 [OBJECT_ID と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/object-id-transact-sql.md)   
 [OBJECT_NAME &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/object-name-transact-sql.md)   
 [sys.objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [TYPEPROPERTY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/typeproperty-transact-sql.md)  
  
  

