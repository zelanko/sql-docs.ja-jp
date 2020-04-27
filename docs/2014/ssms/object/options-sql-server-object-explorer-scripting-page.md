---
title: '[オプション] ([SQL Server オブジェクトエクスプローラー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.ObjectExplorerScripting
- VS.ToolsOptionsPages.Sql_Server_Object_Explorer.ObjectExplorerScripting
ms.assetid: 6105aec9-1b72-4cb2-bd24-fc35f6d95240
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 81e4bafbd596894a8cecbeb707a5d8be698c1f3b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63031936"
---
# <a name="options-sql-server-object-explorer-scripting-page"></a>[オプション] ([SQL Server オブジェクトエクスプローラー] ページ)
  このページを使用すると、 **オブジェクト エクスプローラー**内にあるオブジェクトのコンテキスト メニューの次の各コマンドに適用されるスクリプト オプションを設定できます。  
  
-   ユーザー テーブルおよびビューに対する **[編集]** コマンド。  
  
-   スクリプトオブジェクトは、ユーザーが作成したオブジェクトのコマンド** \<として>** ます。  
  
-   ユーザーが作成したオブジェクトに対する **[変更]** コマンド。  
  
-   このページでは、 **SQL Server スクリプト生成ウィザード**で使用するスクリプト オプションの既定値も設定できます。  
  
## <a name="remarks"></a>解説  
 **Edit**コマンドと**Modify**コマンドを実行すると、同じオプション設定に対し**て [ \<スクリプトオブジェクト>** ] コマンドとは異なる結果が生成される可能性があります。 **[編集]** コマンドおよび **[変更]** コマンドは、クエリ エディター セッション中に現在のデータベースでオブジェクトを変更するために設計されています。 **スクリプト\<オブジェクト> as**コマンドは、後でオブジェクトの作成に使用できるようにスクリプトを生成するように設計されています。  
  
## <a name="options"></a>オプション  
 スクリプト オプションを指定するには、各オプションの右にあるリストから、いずれかの設定を選択します。  
  
### <a name="general-scripting-options"></a>[全般スクリプト作成オプション]  
 **[各ステートメントを区切る]**  
 バッチ区切り記号を使用して、個々の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを区切ります。 **クエリ エディター**の既定のバッチ区切り記号を変更するには、 **[ツール]**/**[オプション]**/**[クエリ実行]**/**[SQL Server]**/**[全般]**/**[バッチ区切り記号]** の順に選択します。 既定値は False です。 詳細については、「 [Transact &#40;transact-sql&#41;](/sql/t-sql/language-elements/sql-server-utilities-statements-go)」を参照してください。  
  
 **[説明用ヘッダーを含める]**  
 スクリプトをオブジェクトごとのセクションに分割し、説明用のコメントを追加します。 既定値は True です。 詳細については、「[コメント &#40;transact-sql&#41;](/sql/t-sql/language-elements/comment-transact-sql)」を参照してください。  
  
 **[VarDecimal オプションを含める]**  
 vardecimal ストレージ オプションを含めます。 既定値は False です。 詳細については、「」および「 [transact-sql&#41;&#40;sp_db_vardecimal_storage_format ](/sql/relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql)」を参照してください。  
  
 **[変更の追跡のスクリプトを作成]**  
 変更の追跡の情報をスクリプトに含めます。  
  
 **[サーバーのバージョン互換のスクリプト]**  
 選択したバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]で実行できるスクリプトを作成します。 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] の新機能のスクリプトを以前のバージョン用に生成することはできません。 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 用に作成したスクリプトには、以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]で動作しているサーバーや、以前の [データベース互換性レベルの設定](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)が適用されているデータベースに対して実行できないものもあります。  
  
 **[フルテキスト カタログのスクリプトを作成]**  
 フルテキスト カタログのスクリプトを含めます。 既定値は False です。 詳細については、「 [transact-sql&#41;&#40;のフルテキストカタログの作成](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)」を参照してください。  
  
 **データベース>\<を使用したスクリプトの作成**  
 スクリプトに USE &lt;データベース&gt; ステートメントを追加することにより、現在の **オブジェクト エクスプローラー** データベースのコンテキストでデータベース オブジェクトを作成します。 スクリプトが別のデータベースで使用される可能性がある場合は、False を選択して除外します。 既定値は True です。 詳細については、「[USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql)」を参照してください。  
  
### <a name="object-scripting-options"></a>[オブジェクト スクリプト作成オプション]  
 **[依存オブジェクトのスクリプトを生成する]**  
 選択したオブジェクトのスクリプトを実行する際に必要な追加オブジェクトのスクリプトを生成します。 既定値は False です。  
  
 **[IF NOT EXISTS 句を含める]**  
 各オブジェクトを作成する前にデータベースにそのオブジェクトが存在しないことを確認するためのステートメントを含めます。 既定値は False です。 詳細について[は、それ以外](/sql/t-sql/language-elements/if-else-transact-sql)の場合は、transact-sql&#41;&#40;transact-sql [&#41;&#40;存在](/sql/t-sql/language-elements/exists-transact-sql)します。  
  
 **[オブジェクト名を修飾するスキーマ]**  
 オブジェクト名をオブジェクト スキーマで修飾します。 既定値は False です。 詳細については、「 [データベース スキーマの作成](../../relational-databases/security/authentication-access/create-a-database-schema.md)」を参照してください。  
  
 **[拡張プロパティのスクリプトを作成]**  
 オブジェクトに拡張プロパティが含まれている場合、それらの拡張プロパティをスクリプトに追加します。 既定値は False です。 詳細については、「[sp_addextendedproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql)」を参照してください。  
  
 **[所有者のスクリプトを作成]**  
 生成されたスクリプトに所有者を含めます。 既定値は False です。  
  
 **[権限のスクリプトを作成]**  
 データベース オブジェクトに対する権限をスクリプトに含めます。 既定値は True です。 詳細については、「[アクセス許可 &#40;データベースエンジン&#41;](../../relational-databases/security/permissions-database-engine.md)」を参照してください。  
  
### <a name="tableview-options"></a>[テーブル/ビュー オプション]  
 次のオプションは、テーブルまたはビューのスクリプトのみに適用されます。  
  
 **[ユーザー定義データ型から基本データ型に変換します]**  
 ユーザー定義データ型を元の基本型に変換します。 スクリプトを実行するデータベースに、ソース データベースのユーザー定義データ型が存在しない場合は、True を使用します。 ユーザー定義データ型を保持する場合は、False を使用します。 既定値は False です。 詳細については、[CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql)を参照してください。  
  
 **[SET ANSI PADDING コマンドを生成する]**  
 各 CREATE TABLE ステートメントの前後に SET ANSI_PADDING ステートメントを追加します。 既定値は True です。 詳細については、「[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql)」を参照してください。  
  
 **[照合順序を含める]**  
 列定義に照合順序を含めます。 既定値は True です。 詳細については、「 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)」を参照してください。  
  
 **[IDENTITY プロパティを含める]**  
 IDENTITY シードおよび IDENTITY インクリメントの定義を含めます。 既定値は True です。 詳細については、「[IDENTITY &#40;プロパティ&#41; &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql-identity-property)」を参照してください。  
  
 **[外部キー参照を修飾するスキーマ]**  
 FOREIGN KEY 制約のテーブル参照にスキーマ名を追加します。 既定値は True です。  
  
 **[バインドされた既定値およびルールのスクリプトを作成]**  
 バインド ストアド プロシージャ **sp_bindefault** および **sp_bindrule** の呼び出しを含めます。 既定値は True です。 詳細については、「 [sp_bindefault &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-bindefault-transact-sql) 」と「 [transact-sql &#40;の sp_bindrule ](/sql/relational-databases/system-stored-procedures/sp-bindrule-transact-sql)」を参照してください。  
  
 **[CHECK 制約のスクリプトを作成]**  
 スクリプトに [CHECK 制約](../../relational-databases/tables/unique-constraints-and-check-constraints.md) を追加します。 既定値は True です。  
  
 **[既定のスクリプトを作成]**  
 スクリプトに列の既定値を含めます。 既定値は False です。 詳細については、「[CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql)」を参照してください。  
  
 **[ファイル グループのスクリプトを作成]**  
 テーブル定義で ON 句にファイル グループを指定します。 既定値は False です。 詳細については、「[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)」を参照してください。  
  
 **[外部キーのスクリプトを作成]**  
 スクリプトに [FOREIGN KEY 制約](../../relational-databases/tables/primary-and-foreign-key-constraints.md) を含めます。 既定値は False です。  
  
 **[フルテキスト インデックスのスクリプトを作成]**  
 スクリプトにフルテキスト インデックスを含めます。 既定値は False です。 詳細については、「 [transact-sql&#41;&#40;のフルテキストインデックスの作成](/sql/t-sql/statements/create-fulltext-index-transact-sql)」を参照してください。  
  
 **[インデックスのスクリプトを作成]**  
 スクリプトにクラスター化、非クラスター化、および XML インデックスを含めます。 既定値は True です。 詳細については、「[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)」を参照してください。  
  
 **[パーティション構成のスクリプトを作成]**  
 スクリプトにテーブル パーティション分割構成を含めます。 既定値は False です。 詳細については、「 [CREATE PARTITION SCHEME &#40;transact-sql&#41;](/sql/t-sql/statements/create-partition-scheme-transact-sql)」を参照してください。  
  
 **[主キーのスクリプトを作成]**  
 スクリプトに [PRIMARY KEY 制約](../../relational-databases/tables/primary-and-foreign-key-constraints.md) を含めます。 既定値は True です。  
  
 **[統計のスクリプトを作成]**  
 スクリプトにユーザー定義統計を含めます。 既定値は False です。 詳細については、「[CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql)」を参照してください。  
  
 **[トリガーのスクリプトを作成]**  
 スクリプトにトリガーを含めます。 既定値は False です。 詳細については、「[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)」を参照してください。  
  
 **[一意キーのスクリプトを作成]**  
 スクリプトに [UNIQUE 制約と CHECK 制約](../../relational-databases/tables/unique-constraints-and-check-constraints.md) を含めます。 既定値は False です。  
  
 **[ビュー列のスクリプトを作成]**  
 ビュー ヘッダーにビュー列を宣言します。 既定値は False です。 詳細については、「[CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql)」を参照してください。  
  
 **[ScriptDriIncludeSystemNames]**  
 宣言参照整合性を適用するために、システムによって生成される制約名を含めます。 既定値は False です。 詳細については、「 [REFERENTIAL_CONSTRAINTS &#40;transact-sql&#41;](/sql/relational-databases/system-information-schema-views/referential-constraints-transact-sql)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [スクリプトの生成 &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/generate-scripts-sql-server-management-studio.md)  
  
  
