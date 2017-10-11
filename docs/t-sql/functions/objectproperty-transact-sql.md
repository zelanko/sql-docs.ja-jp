---
title: "OBJECTPROPERTY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OBJECTPROPERTY
- OBJECTPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- displaying schema-scoped object information
- viewing schema-scoped object information
- OBJECTPROPERTY function
- schema-scoped objects [SQL Server]
- objects [SQL Server], schema-scoped
ms.assetid: 27569888-f8b5-4cec-a79f-6ea6d692b4ae
caps.latest.revision: 81
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0ee3350b200f0f42203a89d06ddb587b0792ee18
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="objectproperty-transact-sql"></a>OBJECTPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベース内のスキーマ スコープ オブジェクトに関する情報を返します。 スキーマ スコープ オブジェクトの一覧は、次を参照してください。 [sys.objects & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md). データ定義言語 (DDL) トリガーやイベント通知など、スキーマ スコープ オブジェクト以外のオブジェクトについては、この関数を使用できません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
OBJECTPROPERTY ( id , property )   
```  
  
## <a name="arguments"></a>引数  
 *id*  
 現在のデータベース内のオブジェクトの ID を表す式を指定します。 *id*は**int**は現在のデータベース コンテキストでのスキーマ スコープ オブジェクトであると仮定します。  
  
 *プロパティ*  
 指定されたオブジェクトに対して返される情報を表す式は、 *id*です。*プロパティ*値は次のいずれかになります。  
  
> [!NOTE]  
>  明記しない限り、NULL が返されます*プロパティ*有効なプロパティ名ではない*id* 、有効なオブジェクト ID ではありません*id*は、指定された、サポートされていないオブジェクト型です。*プロパティ*、か、呼び出し元に、オブジェクトのメタデータを表示するアクセス許可がありません。  
  
|プロパティ名|オブジェクトの種類|説明と戻り値|  
|-------------------|-----------------|-------------------------------------|  
|CnstIsClustKey|制約|クラスター化インデックスを指定した PRIMARY KEY 制約。<br /><br /> 1 = True<br /><br /> 0 = False|  
|CnstIsColumn|制約|単一の列での、CHECK、DEFAULT、または FOREIGN KEY 制約。<br /><br /> 1 = True<br /><br /> 0 = False|  
|CnstIsDeleteCascade|制約|ON DELETE CASCADE オプションを指定した FOREIGN KEY 制約。<br /><br /> 1 = True<br /><br /> 0 = False|  
|CnstIsDisabled|制約|制約の無効化。<br /><br /> 1 = True<br /><br /> 0 = False|  
|CnstIsNonclustKey|制約|非クラスター化インデックスを持つ PRIMARY KEY 制約または UNIQUE 制約。<br /><br /> 1 = True<br /><br /> 0 = False|  
|CnstIsNotRepl|制約|制約を NOT FOR REPLICATION キーワードを使って定義。<br /><br /> 1 = True<br /><br /> 0 = False|  
|CnstIsNotTrusted|制約|既存の行を確認せずに制約が有効化されているので、制約がすべての行に対応しているとは限りません。<br /><br /> 1 = True<br /><br /> 0 = False|  
|CnstIsUpdateCascade|制約|ON UPDATE CASCADE オプションを指定した FOREIGN KEY 制約。<br /><br /> 1 = True<br /><br /> 0 = False|  
|ExecIsAfterTrigger|トリガー|AFTER トリガー。<br /><br /> 1 = True<br /><br /> 0 = False|  
|ExecIsAnsiNullsOn|[!INCLUDE[tsql](../../includes/tsql-md.md)]関数、[!INCLUDE[tsql](../../includes/tsql-md.md)]プロシージャ[!INCLUDE[tsql](../../includes/tsql-md.md)]トリガー、ビュー|作成時における ANSI_NULLS の設定。<br /><br /> 1 = True<br /><br /> 0 = False|  
|ExecIsDeleteTrigger|トリガー|DELETE トリガー。<br /><br /> 1 = True<br /><br /> 0 = False|  
|ExecIsFirstDeleteTrigger|トリガー|最初のトリガーがテーブルに対して DELETE を実行したときに発生します。<br /><br /> 1 = True<br /><br /> 0 = False|  
|ExecIsFirstInsertTrigger|トリガー|最初のトリガーがテーブルに対して INSERT を実行したときに発生します。<br /><br /> 1 = True<br /><br /> 0 = False|  
|ExecIsFirstUpdateTrigger|トリガー|最初のトリガーがテーブルに対して UPDATE を実行したときに発生します。<br /><br /> 1 = True<br /><br /> 0 = False|  
|ExecIsInsertTrigger|トリガー|INSERT トリガー。<br /><br /> 1 = True<br /><br /> 0 = False|  
|ExecIsInsteadOfTrigger|トリガー|INSTEAD OF トリガー。<br /><br /> 1 = True<br /><br /> 0 = False|  
|ExecIsLastDeleteTrigger|トリガー|テーブルに対して DELETE を実行するときに最後に起動されるトリガー。<br /><br /> 1 = True<br /><br /> 0 = False|  
|ExecIsLastInsertTrigger|トリガー|テーブルに対して INSERT を実行するときに最後に起動されるトリガー。<br /><br /> 1 = True<br /><br /> 0 = False|  
|ExecIsLastUpdateTrigger|トリガー|テーブルに対して UPDATE を実行するときに最後に起動されるトリガー。<br /><br /> 1 = True<br /><br /> 0 = False|  
|ExecIsQuotedIdentOn|[!INCLUDE[tsql](../../includes/tsql-md.md)]関数、[!INCLUDE[tsql](../../includes/tsql-md.md)]プロシージャ[!INCLUDE[tsql](../../includes/tsql-md.md)]トリガー、ビュー|作成時における QUOTED_IDENTIFIER の設定。<br /><br /> 1 = True<br /><br /> 0 = False|  
|ExecIsStartup|手順|スタートアップ プロシージャ。<br /><br /> 1 = True<br /><br /> 0 = False|  
|ExecIsTriggerDisabled|トリガー|トリガーの無効化。<br /><br /> 1 = True<br /><br /> 0 = False|  
|ExecIsTriggerNotForRepl|トリガー|NOT FOR REPLICATION として定義されているトリガー。<br /><br /> 1 = True<br /><br /> 0 = False|  
|ExecIsUpdateTrigger|トリガー|UPDATE トリガー。<br /><br /> 1 = True<br /><br /> 0 = False|  
|ExecIsWithNativeCompilation|[!INCLUDE[tsql](../../includes/tsql-md.md)] プロシージャ|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> プロシージャはネイティブでコンパイルされます。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**|  
|HasAfterTrigger|テーブル、ビュー|テーブルまたはビューに AFTER トリガーがあります。<br /><br /> 1 = True<br /><br /> 0 = False|  
|HasDeleteTrigger|テーブル、ビュー|テーブルまたはビューに DELETE トリガーがあります。<br /><br /> 1 = True<br /><br /> 0 = False|  
|HasInsertTrigger|テーブル、ビュー|テーブルまたはビューに INSERT トリガーがあります。<br /><br /> 1 = True<br /><br /> 0 = False|  
|HasInsteadOfTrigger|テーブル、ビュー|テーブルまたはビューに INSTEAD OF トリガーがあります。<br /><br /> 1 = True<br /><br /> 0 = False|  
|HasUpdateTrigger|テーブル、ビュー|テーブルまたはビューに UPDATE トリガーがあります。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsAnsiNullsOn|[!INCLUDE[tsql](../../includes/tsql-md.md)]関数、[!INCLUDE[tsql](../../includes/tsql-md.md)]プロシージャ、テーブル、[!INCLUDE[tsql](../../includes/tsql-md.md)]トリガー、ビュー|テーブルの ANSI NULLS オプションが ON に設定されていることを指定します。 つまり、NULL 値との比較結果はすべて UNKNOWN になります。 この設定は、テーブルが存在する限り、計算列や制約をはじめとするテーブル定義内のすべての式に適用されます。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsCheckCnst|任意のスキーマ スコープ オブジェクト|CHECK 制約。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsConstraint|任意のスキーマ スコープ オブジェクト|列またはテーブルに対する単一列の CHECK、DEFAULT、または FOREIGN KEY 制約です。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsDefault|任意のスキーマ スコープ オブジェクト|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 既定のバインド。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsDefaultCnst|任意のスキーマ スコープ オブジェクト|DEFAULT 制約。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsDeterministic|関数、ビュー|関数またはビューの決定性を示すプロパティ。<br /><br /> 1 = 決定的<br /><br /> 0 = 非決定的|  
|IsEncrypted|[!INCLUDE[tsql](../../includes/tsql-md.md)]関数、[!INCLUDE[tsql](../../includes/tsql-md.md)]プロシージャ、テーブル、[!INCLUDE[tsql](../../includes/tsql-md.md)]トリガー、ビュー|モジュール ステートメントの元のテキストが、暗号化した形式に変換されたことを示します。 難読化の出力内のカタログ ビューのいずれかで直接表示がない[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]です。 システム テーブルまたはデータベース ファイルにアクセスすることがなくユーザーには、難読化されたテキストを取得できません。 ただし、テキストは経由でシステム テーブルにアクセスするか、ユーザーが使用できる、 [DAC ポート](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)または直接データベース ファイルにアクセスします。 また、サーバー プロセスにデバッガーをアタッチできるユーザーは、実行時、元のプロシージャをメモリから取得できます。<br /><br /> 1 = 暗号化<br /><br /> 0 = 暗号化されていません。<br /><br /> 基本データ型: **int**|  
|IsExecuted|任意のスキーマ スコープ オブジェクト|オブジェクトが実行可能かどうかを示します (ビュー、プロシージャ、関数、またはトリガー)。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsExtendedProc|任意のスキーマ スコープ オブジェクト|拡張プロシージャ。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsForeignKey|任意のスキーマ スコープ オブジェクト|FOREIGN KEY 制約。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsIndexed|テーブル、ビュー|インデックス付きのテーブルまたはビュー。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsIndexable|テーブル、ビュー|インデックスを作成できるテーブルまたはビュー。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsInlineFunction|関数|インライン関数。<br /><br /> 1 = インライン関数<br /><br /> 0 = インライン関数ではない|  
|IsMSShipped|任意のスキーマ スコープ オブジェクト|インストール中に作成されたオブジェクト[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsPrimaryKey|任意のスキーマ スコープ オブジェクト|PRIMARY KEY 制約。<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> NULL = 関数ではありません。またはオブジェクト ID が無効です。|  
|IsProcedure|任意のスキーマ スコープ オブジェクト|プロシージャ。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsQuotedIdentOn|[!INCLUDE[tsql](../../includes/tsql-md.md)]関数、[!INCLUDE[tsql](../../includes/tsql-md.md)]プロシージャ、テーブル、[!INCLUDE[tsql](../../includes/tsql-md.md)]トリガー、ビュー、CHECK 制約、DEFAULT 定義|オブジェクトの引用符で囲まれた識別子の設定が ON であることを指定します。 オブジェクト定義に含まれるすべての式の中で、識別子は二重引用符で区切られます。<br /><br /> 1 = ON <br /><br /> 0 = OFF|  
|IsQueue|任意のスキーマ スコープ オブジェクト|Service Broker キュー。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsReplProc|任意のスキーマ スコープ オブジェクト|レプリケーション プロシージャ。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsRule|任意のスキーマ スコープ オブジェクト|ルールのバインド。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsScalarFunction|関数|スカラー値関数。<br /><br /> 1 = スカラー値関数<br /><br /> 0 = スカラー値関数ではない|  
|IsSchemaBound|関数、ビュー|SCHEMABINDING を使用して作成されたスキーマ バインド関数またはビュー。<br /><br /> 1 = スキーマ バインド<br /><br /> 0 = 非スキーマ バインドです。|  
|IsSystemTable|テーブル|システム テーブル。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsTable|テーブル|テーブル。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsTableFunction|関数|テーブル値関数。<br /><br /> 1 = テーブル値関数<br /><br /> 0 = テーブル値関数ではない|  
|IsTrigger|任意のスキーマ スコープ オブジェクト|トリガーです。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsUniqueCnst|任意のスキーマ スコープ オブジェクト|UNIQUE 制約。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsUserTable|テーブル|ユーザー定義テーブル。<br /><br /> 1 = True<br /><br /> 0 = False|  
|IsView|表示|ビュー。<br /><br /> 1 = True<br /><br /> 0 = False|  
|OwnerId|任意のスキーマ スコープ オブジェクト|オブジェクトの所有者です。<br /><br /> **注:**必ずしもオブジェクト所有者がスキーマの所有者ではありません。 たとえば、子オブジェクト (いる*parent_object_id*が null でない) は常に、親と同じ所有者の ID を返します。<br /><br /> NULL 以外 = オブジェクト所有者のデータベース ユーザー ID です。|  
|TableDeleteTrigger|テーブル|テーブルに DELETE トリガーがあります。<br /><br /> >1 = 指定された種類の最初のトリガーの ID|  
|TableDeleteTriggerCount|テーブル|テーブルには指定された数の DELETE トリガーがあります。<br /><br /> >0 = DELETE トリガーの数。|  
|TableFullTextMergeStatus|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 現在マージ中のフルテキスト インデックスがテーブルにあるかどうかを示します。<br /><br /> 0 = テーブルにフルテキスト インデックスがないか、フルテキスト インデックスがマージ中ではない<br /><br /> 1 = フルテキスト インデックスがマージ中|  
|TableFullTextBackgroundUpdateIndexOn|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> テーブルではフルテキスト インデックスのバックグラウンド更新 (変更の自動追跡) が有効です。<br /><br /> 1 = TRUE<br /><br /> 0 = FALSE|  
|TableFulltextCatalogId|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> テーブルのフルテキスト インデックス データが存在する、フルテキスト カタログの ID。<br /><br /> 0 以外 = フルテキスト インデックス テーブル内の行を識別する一意なインデックスに関連付けられた、フルテキスト カタログ ID。<br /><br /> 0 = テーブルにフルテキスト インデックスはない。|  
|TableFulltextChangeTrackingOn|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> テーブルでは、フルテキストの変更の追跡が有効になっています。<br /><br /> 1 = TRUE<br /><br /> 0 = FALSE|  
|TableFulltextDocsProcessed|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> フルテキスト インデックス作成の開始以降に処理された行の数。 フルテキスト検索用にインデックスが作成されるテーブルでは、1 行のすべての列が、インデックスが作成される 1 つのドキュメントの一部と見なされます。<br /><br /> 0 = アクティブ クロールまたはフルテキスト インデックス作成は完了していない<br /><br /> > 0 = 次のいずれか (A または B): A) で処理されたドキュメントの数を挿入または更新操作が開始されてから full、Incremental、または手動の変更を追跡します。 B) 挿入または更新操作の変更の追跡をバック グラウンド更新インデックス作成が有効になっているため、フルテキスト インデックス スキーマの変更、フルテキスト カタログの再構築すると、またはのインスタンスによって処理された行の数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]再起動とにします。<br /><br /> NULL = テーブルにフルテキスト インデックスはない。<br /><br /> このプロパティは、削除された行を監視またはカウントしません。|  
|TableFulltextFailCount|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> フルテキスト検索によるインデックスが設定されなかった行数。<br /><br /> 0 = 作成完了<br /><br /> > 0 = 次のいずれか (A または B): A) Full、Incremental、および手動更新の変更の追跡が開始されてからインデックスが作成されなかったドキュメントの数。 B) の変更の追跡を背景には、インデックス、インデックスを作成の開始または母集団の再起動以降インデックスが作成されなかった行の数を更新します。 これは、スキーマの変更、カタログの再構築、サーバーの再起動などにより発生する場合があります。<br /><br /> NULL = テーブルにフルテキスト インデックスはない。|  
|TableFulltextItemCount|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> フルテキスト インデックスが正常に設定された行数。|  
|TableFulltextKeyColumn|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> フルテキスト インデックス定義に関係している、一意な単一列インデックスに関連付けられた列の ID。<br /><br /> 0 = テーブルにフルテキスト インデックスはない。|  
|TableFulltextPendingChanges|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 変更の追跡が処理されていないエントリ数。<br /><br /> 0 = 変更の追跡は有効でない<br /><br /> NULL = テーブルにフルテキスト インデックスはない。|  
|TableFulltextPopulateStatus|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 0 = アイドル状態<br /><br /> 1 = 全体を作成中<br /><br /> 2 = 増分作成中<br /><br /> 3 = 追跡した変更を伝達中<br /><br /> 4 = バック グラウンド更新インデックスは、自動変更の追跡などの進行中です。<br /><br /> 5 = フルテキスト インデックス作成が絞り込みまたは停止された|  
|TableHasActiveFulltextIndex|テーブル|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> テーブルにアクティブなフルテキスト インデックスがあります。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableHasCheckCnst|テーブル|テーブルに CHECK 制約があります。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableHasClustIndex|テーブル|テーブルにクラスター化インデックスがあります。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableHasDefaultCnst|テーブル|テーブルに DEFAULT 制約があります。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableHasDeleteTrigger|テーブル|テーブルに DELETE トリガーがあります。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableHasForeignKey|テーブル|テーブルに FOREIGN KEY 制約があります。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableHasForeignRef|テーブル|テーブルは FOREIGN KEY 制約により参照されています。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableHasIdentity|テーブル|テーブルに ID 列があります。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableHasIndex|テーブル|テーブルに任意の種類のインデックスがあります。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableHasInsertTrigger|テーブル|オブジェクトに INSERT トリガーがあります。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableHasNonclustIndex|テーブル|テーブルには非クラスター化インデックスがあります。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableHasPrimaryKey|テーブル|テーブルに主キーがあります。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableHasRowGuidCol|テーブル|テーブルの ROWGUIDCOL には、 **uniqueidentifier**列です。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableHasTextImage|テーブル|テーブルには、**テキスト**、 **ntext**、または**イメージ**列です。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableHasTimestamp|テーブル|テーブルには、**タイムスタンプ**列です。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableHasUniqueCnst|テーブル|テーブルに UNIQUE 制約があります。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableHasUpdateTrigger|テーブル|オブジェクトには UPDATE トリガーがあります。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableHasVarDecimalStorageFormat|テーブル|テーブルが有効になって**vardecimal**ストレージ形式です。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableInsertTrigger|テーブル|テーブルに INSERT トリガーがあります。<br /><br /> >1 = 指定された種類の最初のトリガーの ID|  
|TableInsertTriggerCount|テーブル|テーブルには指定された数の INSERT トリガーがあります。<br /><br /> >0 = INSERT トリガーの数|  
|TableIsFake|テーブル|テーブルは実在せず、 オンデマンドで内部的に具体化されて、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]です。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableIsLockedOnBulkLoad|テーブル|ためにテーブルがロックされている、 **bcp**または BULK INSERT ジョブです。<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableIsMemoryOptimized|テーブル|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> テーブルはメモリ最適化されています<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> 基本データ型: **int**<br /><br /> 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。|  
|TableIsPinned|テーブル|テーブルは固定され、データ キャッシュに確保されています。<br /><br /> 0 = False<br /><br /> この機能はサポートされていません[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]およびそれ以降。|  
|TableTextInRowLimit|テーブル|Text in row で許可される最大バイト数。<br /><br /> text in row オプションが設定されていない場合は 0 です。|  
|TableUpdateTrigger|テーブル|テーブルに UPDATE トリガーがあります。<br /><br /> > 1 = 指定された種類の最初のトリガーの ID|  
|TableUpdateTriggerCount|テーブル|テーブルには指定された数の UPDATE トリガーがあります。<br /><br /> > 0 = UPDATE トリガーの数|  
|TableHasColumnSet|テーブル|テーブルに列セットがあります。<br /><br /> 0 = False<br /><br /> 1 = True<br /><br /> 詳細については、「 [列セットの使用](../../relational-databases/tables/use-column-sets.md)」を参照してください。|  
|TableTemporalType|テーブル|**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> テーブルの種類を指定します。<br /><br /> 0 = 非一時的なテーブル<br /><br /> 1 = システムのバージョン情報のテーブルの履歴テーブル<br /><br /> 2 = システムのバージョン情報の一時的なテーブル|  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="exceptions"></a>例外  
 エラーが発生した場合、または呼び出し元にオブジェクトの表示権限がない場合は、NULL が返されます。  
  
 ユーザーが所有しているか、または権限を与えられている、セキュリティ保護可能なリソースのメタデータのみを表示できます。 つまり、オブジェクトに対する権限がユーザーに与えられていない場合、メタデータを生成する組み込み関数 (OBJECTPROPERTY など) が NULL を返す可能性があります。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]であると推定*object_id*が現在のデータベース コンテキスト。 参照するクエリ、 *object_id*別のデータベースで NULL または不適切な結果が返されます。 たとえば、次のクエリでは現在のデータベース コンテキストは、マスター データベースです。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]を指定されたプロパティの値を返そう*object_id*クエリで指定されたデータベースではなく、そのデータベースにします。 クエリが正しくない結果を返しますビュー `vEmployee` master データベースに含まれない。  
  
```  
USE master;  
GO  
SELECT OBJECTPROPERTY(OBJECT_ID(N'AdventureWorks2012.HumanResources.vEmployee'), 'IsView');  
GO  
```  
  
 OBJECTPROPERTY (*view_id*、'IsIndexable') IsIndexable プロパティの評価は、ビュー定義、正規化、および部分最適化の解析が必要なために、多くのコンピューター リソースを使用することがあります。 IsIndexable プロパティではインデックスを作成できるテーブルまたはビューを指定しますが、特定のインデックス キーの要件が満たされない場合、インデックスの実際の作成は失敗します。 詳細については、「[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)」を参照してください。  
  
 OBJECTPROPERTY (*table_id*、'TableHasActiveFulltextIndex') はインデックス作成のため、テーブルの少なくとも 1 つの列が追加されたときに 1 (true) の値を返します。 インデックス作成で先頭の列が追加されるとすぐ、フルテキスト インデックス作成が自動的にアクティブになります。  
  
 テーブルを作成するときに QUOTED IDENTIFIER オプションが OFF に設定されている場合でも、作成されるテーブルのメタデータでは、このオプションは常に ON として格納されます。 したがって、OBJECTPROPERTY (*table_id*、'IsQuotedIdentOn') は常に 1 (true) の値を返します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-verifying-that-an-object-is-a-table"></a>A. オブジェクトがテーブルかどうかを確認する  
 次の例では、`UnitMeasure` が [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースのテーブルかどうかをテストします。  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECTPROPERTY (OBJECT_ID(N'Production.UnitMeasure'),'ISTABLE') = 1  
   PRINT 'UnitMeasure is a table.'  
ELSE IF OBJECTPROPERTY (OBJECT_ID(N'Production.UnitMeasure'),'ISTABLE') = 0  
   PRINT 'UnitMeasure is not a table.'  
ELSE IF OBJECTPROPERTY (OBJECT_ID(N'Production.UnitMeasure'),'ISTABLE') IS NULL  
   PRINT 'ERROR: UnitMeasure is not a valid object.';  
GO  
  
```  
  
### <a name="b-verifying-that-a-scalar-valued-user-defined-function-is-deterministic"></a>B. スカラー値ユーザー定義関数の決定性を確認する  
 次の例をテストするかどうか、ユーザー定義のスカラー値関数`ufnGetProductDealerPrice`を返す、 **money**値が決定的でします。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT OBJECTPROPERTY(OBJECT_ID('dbo.ufnGetProductDealerPrice'), 'IsDeterministic');  
GO  
```  
  
 結果セットを表示する`ufnGetProductDealerPrice`決定的関数ではありません。  
  
 ```
-----  
0
```  
  
### <a name="c-finding-the-objects-that-belong-to-a-specific-schema"></a>C. 特定のスキーマに属するオブジェクトを見つける  
 次の例では、`SchemaId` プロパティを使用して、スキーマ `Production` に属するすべてのオブジェクトを返します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT name, object_id, type_desc  
FROM sys.objects   
WHERE OBJECTPROPERTY(object_id, N'SchemaId') = SCHEMA_ID(N'Production')  
ORDER BY type_desc, name;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-verifying-that-an-object-is-a-table"></a>D: オブジェクトがテーブルでことを確認しています  
 次の例では、`dbo.DimReseller` が [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] データベースのテーブルかどうかをテストします。  
  
```  
-- Uses AdventureWorks  
  
IF OBJECTPROPERTY (OBJECT_ID(N'dbo.DimReseller'),'ISTABLE') = 1  
   SELECT 'DimReseller is a table.'  
ELSE   
   SELECT 'DimReseller is not a table.';  
GO  
```  
  
### <a name="e-finding-the-tables-that-belong-to-a-specific-schema"></a>E: の特定のスキーマに属しているテーブルの検索  
 次の例では、dbo スキーマにすべてのテーブルを返します。  
  
```  
-- Uses AdventureWorks  
  
SELECT name, object_id, type_desc  
FROM sys.objects   
WHERE OBJECTPROPERTY(object_id, N'SchemaId') = SCHEMA_ID(N'dbo')  
ORDER BY type_desc, name;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [COLUMNPROPERTY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/columnproperty-transact-sql.md)   
 [メタデータ関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [OBJECTPROPERTYEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/objectpropertyex-transact-sql.md)   
 [ALTER AUTHORIZATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [TYPEPROPERTY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/typeproperty-transact-sql.md)   
 [sys.objects & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  


