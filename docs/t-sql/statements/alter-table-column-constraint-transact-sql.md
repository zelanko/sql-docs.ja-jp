---
title: "column_constraint (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/05/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- column_constraint
- column_constraint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER TABLE statement
- constraints [SQL Server], properties
- constraints [SQL Server], definitions
- column_constraint
ms.assetid: 8119b7c7-e93b-4de5-8f71-c3b7c70b993c
caps.latest.revision: 54
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a4f8238266e82aadeee973772266de1c74712f28
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-table-columnconstraint-transact-sql"></a>ALTER TABLE column_constraint (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  使用してテーブルに追加する新しい列定義の一部である PRIMARY KEY、FOREIGN KEY、UNIQUE、または CHECK 制約のプロパティを指定[ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
[ CONSTRAINT constraint_name ]   
{   
    [ NULL | NOT NULL ]   
    { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        [ WITH FILLFACTOR = fillfactor ]   
        [ WITH ( index_option [, ...n ] ) ]  
        [ ON { partition_scheme_name (partition_column_name)   
            | filegroup | "default" } ]   
    | [ FOREIGN KEY ]   
        REFERENCES [ schema_name . ] referenced_table_name   
            [ ( ref_column ) ]   
        [ ON DELETE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ ON UPDATE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ NOT FOR REPLICATION ]   
    | CHECK [ NOT FOR REPLICATION ] ( logical_expression )  
}  
```  
  
## <a name="arguments"></a>引数  
 CONSTRAINT  
 PRIMARY KEY、UNIQUE、FOREIGN KEY、または CHECK 制約の定義の開始を指定します。  
  
 *constraint_name*  
 制約の名前を指定します。 制約名の規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md),、名前に番号記号を開始できません点が異なります (#)。 場合*constraint_name*が指定されていない、システムによって生成された名前を割り当て、制約にします。  
  
 NULL | NOT NULL  
 列で NULL 値が許容されるかどうかを指定します。 NULL 値を許可しない列は、既定値が指定されているときだけ追加できます。 新規列が NULL 値を許可し、既定値が指定されていない場合は、テーブル内のすべての行で、新しい列は NULL 値を格納します。 新規列が NULL 値を許可し、新規列と共に既定の定義が追加される場合、WITH VALUES オプションを使用して、テーブル内の既存の各行の新規列に既定値を格納できます。  
  
 新規列が NULL 値を許可しない場合、新規列と共に DEFAULT 定義を追加する必要があります。 新規列は、各既存の行の新規列に既定値と共に自動で読み込まれます。  
  
 列の追加を行うときにテーブルのデータ行に物理的な変更が必要な場合 (各行への DEFAULT 値の追加など)、ALTER TABLE の実行中、ロックはテーブルで保持されます。 これは、ロックが適用されている間にテーブルの内容を変更する機能に影響します。 一方、NULL 値を許可し、既定値を指定しない列の追加は、メタデータ操作に限られ、ロックは関係しません。  
  
 CREATE TABLE または ALTER TABLE を使用すると、データベースとセッションの設定は、列定義で使われているデータ型に NULL 値を許すかどうかの設定に影響を及ぼし、場合によっては、NULL 値を許すかどうかの設定を無効にします。 計算列ではない場合は、常に列を明示的に NULL または NOT NULL として定義することをお勧めします。ユーザー定義データ型を使用する場合は、データ型に NULL 値を許すかどうかの既定の設定を列が使用できるようにすることをお勧めします。 詳細については、「[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)」を参照してください。  
  
 PRIMARY KEY  
 一意のインデックスを使用して、指定された列または列に対してエンティティの整合性を強制する制約です。 PRIMARY KEY 制約は 1 つのテーブルに対して 1 つだけ作成できます。  
  
 UNIQUE  
 一意なインデックスによって、特定の 1 つ以上の列にエンティティの整合性を提供する制約です。  
  
 CLUSTERED | NONCLUSTERED  
 PRIMARY KEY 制約または UNIQUE 制約に対して、クラスター化インデックスまたは非クラスター化インデックスを作成することを指定します。 PRIMARY KEY 制約は既定では CLUSTERED です。 UNIQUE 制約の既定値は NONCLUSTERED です。  
  
 テーブルに既存のクラスター化制約またはクラスター化インデックスがある場合、CLUSTERED は指定できません。 テーブルにクラスター化制約またはクラスター化インデックスが既に存在する場合、PRIMARY KEY 制約には既定で NONCLUSTERED が適用されます。  
  
 列は、 **ntext**、**テキスト**、 **varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、 **xml**、または**イメージ**データ型は、インデックスの列として指定することはできません。  
  
 Fillfactor の値を **=**  *fillfactor*  
 どの程度を指定します、[!INCLUDE[ssDE](../../includes/ssde-md.md)]インデックス データの格納に使用される各インデックス ページを作成する必要があります。 ユーザー指定の fill factor の値は、1 から 100 まで指定できます。 値を指定しない場合の既定値は 0 です。  
  
> [!IMPORTANT]  
>  マニュアルは、WITH FILLFACTOR = *fillfactor* PRIMARY KEY または UNIQUE 制約に適用される唯一のインデックス オプションは、旧バージョンとの互換性のために維持されますが、この方法で、将来的には記載いないようを解放します。 他のインデックス オプションを指定することができます、 [index_option](../../t-sql/statements/alter-table-index-option-transact-sql.md) ALTER TABLE の句。  
  
 ON { *partition_scheme_name***(***partition_column_name***)** | *filegroup*  |  **"**既定**"** }  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 制約に対して作成されるインデックスの格納場所を指定します。 場合*partition_scheme_name*を指定すると、インデックスがパーティション分割し、パーティションで指定されているファイル グループにマップされます*partition_scheme_name*です。 場合*filegroup*を指定すると、名前付きのファイル グループにインデックスを作成します。 場合**"**既定**"**が指定されているか、テーブルと同じファイル グループで、インデックスを作成 ON をまったく指定しない場合。 PRIMARY KEY 制約または UNIQUE 制約のクラスター化インデックスを追加する場合に ON を指定すると、クラスター化インデックスの作成時に、指定したファイル グループにテーブル全体が移動します。  
  
 このコンテキストでは、既定ではない、キーワードです。 既定のファイル グループの識別子を指定しのように区切る必要があります**"**既定**"**または ON **[**既定**]**です。 場合**"**既定**"**を指定すると、現在のセッションの QUOTED_IDENTIFIER オプションが ON をする必要があります。 これが既定の設定です。 詳細については、「[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)」をご覧ください。  
  
 FOREIGN KEY REFERENCES  
 列内のデータに対して参照整合性を提供する制約です。 FOREIGN KEY 制約では、列内の各値が、参照テーブル内の指定された列に含まれていることが必要となります。  
  
 *schema_name*  
 FOREIGN KEY 制約が参照するテーブルが属するスキーマの名前です。  
  
 *referenced_table_name*  
 FOREIGN KEY 制約によって参照されるテーブルを指定します。  
  
 *ref_column*  
 新しい FOREIGN KEY 制約によって参照される、かっこで囲んだ列です。  
  
 削除するときに {**何も**|CASCADE |NULL を設定 |既定値に設定}  
 変更対象のテーブル内の行に参照関係があり、参照先の行が親テーブルから削除された場合に、変更対象のテーブル内の行に対して実行する操作を指定します。 既定値は NO ACTION です。  
  
 NO ACTION  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]エラーと、親テーブル内の行に対して削除操作はロールバックが発生します。  
  
 CASCADE  
 親テーブルから行が削除された場合に、参照元テーブルからもその行が削除されます。  
  
 SET NULL  
 親テーブルの対応する行が削除された場合、外部キーを形成するすべての値が NULL に設定されます。 この制約を実行するには、外部キー列が NULL 値を使用できる必要があります。  
  
 SET DEFAULT  
 親テーブルの対応する行が削除された場合、外部キーを形成するすべての値が既定値に設定されます。 この制約を実行するには、すべての外部キー列に既定値が定義されている必要があります。 列で NULL 値が許容されており、既定値が明示的に設定されていない場合、NULL が列の暗黙的な既定値になります。  
  
 論理レコードを使用するマージ パブリケーションにテーブルを含める場合、CASCADE は使用しないでください。 論理レコードの詳細については、「[論理レコードによる関連行への変更をグループ化](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)」を参照してください。  
  
 変更対象のテーブルに ON DELETE での INSTEAD OF トリガーが既に存在する場合は、ON DELETE CASCADE を定義できません。  
  
 たとえば、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース、 **ProductVendor**テーブルとの参照関係には、**仕入先**テーブル。 **ProductVendor.VendorID**の外部キー参照、 **Vendor.VendorID**主キー。  
  
 内の行で DELETE ステートメントが実行したかどうか、**仕入先**テーブル、および、ON DELETE CASCADE アクションが指定されて**ProductVendor.VendorID**、[!INCLUDE[ssDE](../../includes/ssde-md.md)]に 1 つ以上の従属行を確認します**ProductVendor**テーブル。 内の従属行がある場合、 **ProductVendor**で参照される行だけでなく、テーブルを削除するが、**仕入先**テーブル。  
  
 これに対し、NO ACTION が指定した場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]エラーが発生し、に対する削除操作はロールバック、**仕入先**で少なくとも 1 つの行がある場合、行、 **ProductVendor**それを参照するテーブル。  
  
 更新時に {**何も**|CASCADE |NULL を設定 |既定値に設定}  
 変更対象のテーブル内の行が参照関係を持ち、親テーブルで参照先の行が更新された場合、変更対象のテーブル内の行に対して発生する操作を指定します。 既定値は NO ACTION です。  
  
 NO ACTION  
 NO ACTION を指定すると、[!INCLUDE[ssDE](../../includes/ssde-md.md)]でエラーが発生し、親テーブルの行の更新操作はロールバックされます。  
  
 CASCADE  
 親テーブルで行が更新された場合に、参照元のテーブルでも対応する行が更新されます。  
  
 SET NULL  
 親テーブルの対応する行が更新された場合、外部キーを形成するすべての値が NULL に設定されます。 この制約を実行するには、外部キー列が NULL 値を使用できる必要があります。  
  
 SET DEFAULT  
 親テーブルの対応する行が更新された場合、外部キーを形成するすべての値が既定値に設定されます。 この制約を実行するには、すべての外部キー列に既定値が定義されている必要があります。 列で NULL 値が許容されており、既定値が明示的に設定されていない場合、NULL が列の暗黙的な既定値になります。  
  
 論理レコードを使用するマージ パブリケーションにテーブルを含める場合、CASCADE は使用しないでください。 論理レコードの詳細については、「[論理レコードによる関連行への変更をグループ化](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)」を参照してください。  
  
 変更対象のテーブルに ON UPDATE での INSTEAD OF トリガーが既に存在する場合は、ON UPDATE CASCADE、SET NULL、または SET DEFAULT を定義できません。  
  
 たとえば、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース、 **ProductVendor**テーブルとの参照関係には、**仕入先**テーブル。 **ProductVendor.VendorID**の外部キー参照、 **Vendor.VendorID**主キー。  
  
 内の行で、UPDATE ステートメントが実行したかどうか、**仕入先**テーブルおよび ON UPDATE CASCADE アクションが指定されて**ProductVendor.VendorID**、[!INCLUDE[ssDE](../../includes/ssde-md.md)]に 1 つ以上の従属行を確認します**ProductVendor**テーブル。 存在するかどうか、内の従属行、 **ProductVendor**で参照される行だけでなく、テーブルが更新されます、**仕入先**テーブル。  
  
 これに対し、NO ACTION が指定した場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]エラーが発生し、に対する更新操作はロールバック、**仕入先**で少なくとも 1 つの行がある場合、行、 **ProductVendor**それを参照するテーブル。  
  
 NOT FOR REPLICATION  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 FOREIGN KEY 制約と CHECK 制約に対して指定できます。 制約でこの句を指定すると、レプリケーション エージェントが挿入、更新、削除操作を行う際に制約が適用されません。  
  
 CHECK  
 1 つ以上の列に入力できる値を制限することによってドメインの整合性を設定する制約です。  
  
 *logical_expression*  
 CHECK 制約で使用する論理式を指定します。この式は TRUE または FALSE を返します。 *logical_expression*使用チェック付きの制約が別のテーブルを参照することはできませんが、同じ行の同じテーブル内の他の列を参照できます。 この式では別名データ型は参照できません。  
  
## <a name="remarks"></a>解説  
 FOREIGN 制約または CHECK 制約を追加すると、WITH NOCHECK オプションが指定されない限り、既存のすべてのデータに対して、制約違反の確認が行われます。 違反がある場合、ALTER TABLE は失敗し、エラーが返されます。 既存の列に新しい PRIMARY KEY 制約または UNIQUE 制約を追加するとき、列内のデータは一意であることが必要です。 重複する値が見つかると、ALTER TABLE は失敗します。 PRIMARY KEY 制約または UNIQUE 制約を追加する場合、WITH NOCHECK オプションによる影響はありません。  
  
 PRIMARY KEY 制約と UNIQUE 制約では、それぞれインデックスが生成されます。 UNIQUE 制約と PRIMARY KEY 制約によって生成されるテーブル上のインデックスの個数は、999 個の非クラスター化インデックスと 1 つのクラスター化インデックスに収まる必要があります。 外部キー制約では、自動的にインデックスが生成されることはありません。 ただし、クエリ内で、一方のテーブルの外部キー制約内の列を、他方のテーブルの主キー列または一意なキー列と照合することによって、クエリ内の結合条件で外部キー列は頻繁に使用されます。 外部キー列のインデックスを使用すると、[!INCLUDE[ssDE](../../includes/ssde-md.md)]により、外部キー テーブルの関連データがすばやく検索されます。  
  
## <a name="examples"></a>使用例  
 例については、次を参照してください。 [ALTER TABLE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-table-transact-sql.md).  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [column_definition &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-column-definition-transact-sql.md)  
  
  

