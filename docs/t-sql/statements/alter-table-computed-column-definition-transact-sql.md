---
title: "computed_column_definition (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords: ALTER TABLE statement
ms.assetid: 746eabda-3b4f-4940-b0b5-1c379f5cf7a5
caps.latest.revision: "62"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: faff7cbb4f4eec1cf68601805d0dbbe1a3a84b3e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="alter-table-computedcolumndefinition-transact-sql"></a>ALTER TABLE computed_column_definition (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  使用してテーブルに追加される計算列のプロパティを指定[ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
column_name AS computed_column_expression  
[ PERSISTED [ NOT NULL ] ]  
[   
    [ CONSTRAINT constraint_name ]  
    { PRIMARY KEY | UNIQUE }  
        [ CLUSTERED | NONCLUSTERED ]  
        [ WITH FILLFACTOR = fillfactor ]  
        [ WITH ( <index_option> [, ...n ] ) ]  
        [ ON { partition_scheme_name ( partition_column_name ) | filegroup   
            | "default" } ]  
    | [ FOREIGN KEY ]   
        REFERENCES ref_table [ ( ref_column ) ]   
        [ ON DELETE { NO ACTION | CASCADE } ]   
        [ ON UPDATE { NO ACTION } ]   
        [ NOT FOR REPLICATION ]   
    | CHECK [ NOT FOR REPLICATION ] ( logical_expression )  
]  
```  
  
## <a name="arguments"></a>引数  
*column_name*  
 変更、追加、または削除する列の名前を指定します。 *column_name* 1 ~ 128 文字を指定できます。 新しい列の*column_name*で作成される列は省略できます、**タイムスタンプ**データ型。 ない場合は*column_name*が指定されて、**タイムスタンプ**データ型の列、名前**タイムスタンプ**を使用します。  
  
*computed_column_expression*  
 計算列の値を定義する式です。 計算列は仮想列であり、テーブル内に物理的に格納されている列ではありません。したがって、式を基にして同じテーブル内の別の列を使用して計算されます。 たとえば、計算列は cost AS price * qty のように定義できます。式には、非計算列の名前、定数、関数、および変数のほか、これらを 1 つ以上の演算子によって結合した組み合わせを使用できます。 式は、サブクエリまたは別名データ型を含めることはできません。  
  
 計算列は、選択リスト、WHERE 句、ORDER BY 句、および正規表現を使用できるその他の場所で使用できます。ただし、次の場合は除きます。  
  
-   計算列は、DEFAULT 制約定義または FOREIGN KEY 制約定義として使用したり、NOT NULL 制約定義と共に使用したりすることはできません。 ただし、計算列の値が決定的な式によって定義され、その結果のデータ型がインデックス列で可能な場合、計算列は、インデックスのキー列として、または任意の PRIMARY KEY 制約または UNIQUE 制約の一部として使用できます。  
  
     たとえば、テーブルに整数型の列 a と b がある場合、計算列 a + b にはインデックスを作成できますが、計算列 a+DATEPART(dd, GETDATE()) にインデックスを作成することはできません。これは、この計算列の値が次以降の呼び出しで変更される可能性があるためです。  
  
-   計算列を INSERT ステートメントまたは UPDATE ステートメントの対象にすることはできません。  
  
    > [!NOTE]  
    >  テーブル内の各行は、計算列に含まれる列について、異なる値を格納している可能性があるため、計算列の結果がすべての行で同じとは限りません。  
  
PERSISTED  
 指定する、[!INCLUDE[ssDE](../../includes/ssde-md.md)]は物理的に、テーブルに計算値を格納し、計算列が依存するその他の列が更新されたときに、値を更新します。 計算列に PERSISTED とマークを付けることで、計算列に対し、完全ではないものの決定性のあるインデックスを作成することができます。 詳細については、「 [計算列のインデックス](../../relational-databases/indexes/indexes-on-computed-columns.md)」を参照してください。 パーティション テーブルのパーティション分割列として使用する計算列は、明示的に PERSISTED のマークを付ける必要があります。 *computed_column_expression* PERSISTED が指定されている場合は決定的である必要があります。  
NULL | NOT NULL  
 列で null 値を許容するかどうかを指定します。 NULL は厳密に制約ではありませんが、NOT のように指定することができます NULL です。 計算列で NOT NULL を指定できるのは、同時に PERSISTED も指定した場合だけです。  
  
CONSTRAINT  
 PRIMARY KEY または UNIQUE 制約の定義の開始を指定します。  
  
*constraint_name*  
 新しい制約です。 制約名の規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md),、名前に番号記号を開始できません点が異なります (#)。 場合*constraint_name*が指定されていない、システムによって生成された名前を割り当て、制約にします。  
  
PRIMARY KEY  
 一意のインデックスを使用して、指定された列または列に対してエンティティの整合性を強制する制約です。 PRIMARY KEY 制約は 1 つのテーブルに対して 1 つだけ作成できます。  
  
UNIQUE  
 一意なインデックスによって、指定した 1 つ以上の列にエンティティの整合性を持たせる制約です。  
  
CLUSTERED | NONCLUSTERED  
 PRIMARY KEY 制約または UNIQUE 制約に対して、クラスター化インデックスまたは非クラスター化インデックスを作成することを指定します。 PRIMARY KEY 制約は既定では CLUSTERED です。 UNIQUE 制約の既定値は NONCLUSTERED です。  
  
 テーブルに既存のクラスター化制約またはクラスター化インデックスがある場合、CLUSTERED は指定できません。 テーブルにクラスター化制約またはクラスター化インデックスが既に存在する場合、PRIMARY KEY 制約には既定で NONCLUSTERED が適用されます。  
  
FILLFACTOR =*fillfactor*  
 どの程度を指定します、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]インデックス データの格納に使用される各インデックス ページを作成する必要があります。 ユーザーが指定した*fillfactor* 1 ~ 100 の値を指定できます。 値を指定しない場合の既定値は 0 です。  
  
> [!IMPORTANT]  
>  マニュアルは、WITH FILLFACTOR = *fillfactor* PRIMARY KEY または UNIQUE 制約に適用される唯一のインデックス オプションは、旧バージョンとの互換性のために維持されますが、この方法で、将来的には記載いないようを解放します。 他のインデックス オプションを指定することができます、 [index_option &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-table-index-option-transact-sql.md) ALTER TABLE の句。  
  
FOREIGN KEY REFERENCES  
 1 つ以上の列内のデータに参照整合性を持たせる制約です。 FOREIGN KEY 制約では、列内の各値が、参照されるテーブル内のその値に対応する参照される列に存在している必要があります。 FOREIGN KEY 制約は、参照されるテーブル内の PRIMARY KEY 制約または UNIQUE 制約である列、または参照されるテーブルの UNIQUE INDEX で参照される列のみを参照できます。 計算列の外部キーには、PERSISTED も設定する必要があります。  
  
*ref_table*  
 FOREIGN KEY 制約によって参照されるテーブルの名前です。  
  
(*ref_column* )  
 FOREIGN KEY 制約によって参照されるテーブルの列です。  
  
削除するときに {**何も**|CASCADE}  
 テーブルの行が参照関係を持ち、参照される行が親テーブルから削除された場合に、その行に対して実行される操作を指定します。 既定値は NO ACTION です。  
  
NO ACTION  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]エラーと、親テーブル内の行に対して削除操作はロールバックが発生します。  
CASCADE  
 親テーブルから行が削除された場合に、参照元テーブルからもその行が削除されます。  
  
 たとえば、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースで、ProductVendor テーブルに Vendor テーブルとの参照関係があるとします。 ここで、ProductVendor.BusinessEntityID 外部キーは Vendor.BusinessEntityID 主キーを参照します。  
  
 DELETE ステートメントを Vendor テーブルの行で実行した場合、ON DELETE CASCADE アクションが ProductVendor.BusinessEntityID に対して指定されていると、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では ProductVendor テーブルに 1 つ以上の従属行があるかどうかが確認されます。 従属行がある場合、ProductVendor テーブルの従属行が、Vendor テーブルで参照される行と共に削除されます。  
  
 これに対し、NO ACTION を指定した場合は、ProductVendor テーブルに Vendor テーブルの行を参照する行が 1 つでもあると、[!INCLUDE[ssDE](../../includes/ssde-md.md)]ではエラーが発生し、Vendor テーブルの行に対する削除操作はロールバックされます。  
  
 論理レコードを使用するマージ パブリケーションにテーブルを含める場合、CASCADE は使用しないでください。 論理レコードの詳細については、「[論理レコードによる関連行への変更をグループ化](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)」を参照してください。  
  
更新時に {**何も**}  
 作成されたテーブル内の行が参照関係を持ち、親テーブルで参照先の行が更新された場合、作成されたテーブル内の行に対して発生する操作を指定します。 NO ACTION が指定されている場合、ProductVendor テーブルに Vendor テーブルの行を参照する行が 1 つでもあると、[!INCLUDE[ssDE](../../includes/ssde-md.md)]でエラーが発生し、Vendor 行の更新操作がロールバックされます。  
  
NOT FOR REPLICATION  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 FOREIGN KEY 制約と CHECK 制約に対して指定できます。 制約でこの句を指定すると、レプリケーション エージェントが挿入、更新、削除操作を行う際に制約が適用されません。  
  
CHECK  
 1 つ以上の列に入力できる値を制限することによってドメインの整合性を設定する制約です。 計算列の CHECK 制約には、PERSISTED も設定する必要があります。  
  
*logical_expression*  
 TRUE または FALSE を返す論理式です。 この式には、別名データ型の参照を含めることはできません。  
  
ON { *partition_scheme_name*(*partition_column_name*) |*filegroup*|"default"}  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 制約に対して作成されるインデックスの格納場所を指定します。 場合*partition_scheme_name*を指定すると、インデックスがパーティション分割し、パーティションで指定されているファイル グループにマップされます*partition_scheme_name*です。 場合*filegroup*を指定すると、名前付きのファイル グループにインデックスを作成します。 "default" を指定するか、ON を指定しなかった場合、インデックスはテーブルと同じファイル グループに作成されます。 PRIMARY KEY 制約または UNIQUE 制約のクラスター化インデックスを追加する場合に ON を指定すると、クラスター化インデックスの作成時に、指定したファイル グループにテーブル全体が移動します。  
  
> [!NOTE]  
>  ここでは、default はキーワードではありません。 default は、既定ファイル グループの識別子なので、ON "default" または ON [default] のように区切る必要があります。 "default" を指定する場合は、現在のセッションに対して QUOTED_IDENTIFIER オプションが ON である必要があります。 これが既定の設定です。 詳細については、「[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)」をご覧ください。  
  
## <a name="remarks"></a>解説  
 PRIMARY KEY 制約と UNIQUE 制約では、それぞれインデックスが生成されます。 UNIQUE 制約と PRIMARY KEY 制約によって生成されるテーブル上のインデックスの個数は、999 個の非クラスター化インデックスと 1 つのクラスター化インデックスに収まる必要があります。  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
  
