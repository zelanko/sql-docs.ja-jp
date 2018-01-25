---
title: "DBCC CHECKIDENT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHECKIDENT
- DBCC CHECKIDENT
- CHECKIDENT_TSQL
- DBCC_CHECKIDENT_TSQL
dev_langs: TSQL
helpviewer_keywords:
- checking identity values
- reseeding identity values
- resetting identity values
- identity values [SQL Server]
- identity values [SQL Server], checking
- modifying identity values
- current identity values
- DBCC CHECKIDENT statement
- identity values [SQL Server], reseeding
- reporting current identity values
ms.assetid: 2c00ee51-2062-4e47-8b19-d90f524c6427
caps.latest.revision: "63"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Active
ms.openlocfilehash: 0a370a89e175a00f33d26992cfc5c6aaecbd7436
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-checkident-transact-sql"></a>DBCC CHECKIDENT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  指定された [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のテーブルの現在の ID 値をチェックし、必要に応じて ID 値を変更します。 ID 列の新しい現在の ID 値を手動で設定する場合に DBCC CHECKIDENT を使用することもできます。  
   
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DBCC CHECKIDENT   
 (   
    table_name  
        [, { NORESEED | { RESEED [, new_reseed_value ] } } ]  
)  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>引数  
 *table_name*  
 現在の ID 値をチェックするテーブルの名前を指定します。 指定されたテーブルには、ID 列が含まれている必要があります。 テーブル名は、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。 'Person.AddressType'、または [Person.AddressType] など、2 つまたは 3 つの部分名を区切る必要があります。   
  
 NORESEED  
 現在の ID 値を変更しないように指定します。  
  
 RESEED  
 現在の ID 値を変更するように指定します。  
  
 *new_reseed_value*  
 ID 列の現在値として使用する新しい値を指定します。  
  
 WITH NO_INFOMSGS  
 すべての情報メッセージを表示しないようにします。  
  
## <a name="remarks"></a>解説  
 現在の ID 値に加えられる個々の修正は、指定されているパラメーターによって異なります。  
  
|DBCC CHECKIDENT コマンド|加えられる ID の修正|  
|-----------------------------|---------------------------------------------|  
|DBCC CHECKIDENT ( *table_name*NORESEED)|現在の ID 値はリセットされません。 DBCC CHECKIDENT は、ID 列の現在の ID 値と現在の最大値を返します。 2 つの値が異なる場合は、エラーが発生しないよう、または連続値の一部が欠落しないように、ID 値をリセットする必要があります。|  
|DBCC CHECKIDENT ( *table_name* )<br /><br /> または<br /><br /> DBCC CHECKIDENT ( *table_name*、RESEED)|テーブルの現在の ID 値が、ID 列に格納されている最大の ID 値より小さい場合、テーブルの現在の ID 値は ID 列の最大値にリセットされます。 後の「例外」のセクションを参照してください。|  
|DBCC CHECKIDENT ( *table_name*、RESEED, *new_reseed_value* )|現在の id 値に設定されている、 *new_reseed_value*です。 行が挿入されていないテーブルにテーブルが作成された、またはすべての行が削除された場合、TRUNCATE TABLE ステートメントを使用して、DBCC CHECKIDENT を実行した後に挿入された最初の行を使用して場合*new_reseed_value* id として。<br /><br /> 次の行が挿入された行がテーブルに存在する場合、 *new_reseed_value*値。 バージョンで[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]以前で、次の行の挿入を使用して*new_reseed_value* +[現在インクリメント](../../t-sql/functions/ident-incr-transact-sql.md)値。<br /><br /> テーブルが空でない場合、ID 値に ID 列の最大値より小さな値を設定すると、次の状況のいずれかが発生する可能性があります。<br /><br /> Id 列に PRIMARY KEY または UNIQUE 制約が存在する場合エラー メッセージ 2627 が生成されますテーブルへの後続の挿入操作で生成される id 値が既存の値と競合するためです。<br /><br /> PRIMARY KEY または UNIQUE 制約が存在しない場合、後続の挿入操作は重複した id 値になります。|  
  
## <a name="exceptions"></a>例外  
 次の表に、DBCC CHECKIDENT で現在の ID 値が自動的にリセットされないときの条件と、ID 値をリセットする方法を示します。  
  
|条件|リセット方法|  
|---------------|-------------------|  
|現在の ID 値がテーブルの最大値より大きい。|DBCC checkident (*table_name*、NORESEED) の列で、現在の最大値を確認し、その値としてを指定、 *new_reseed_value* DBCC checkident (*table _名前*、RESEED,*new_reseed_value*) コマンド。<br /><br /> - または -<br /><br /> DBCC checkident (*table_name*、RESEED,*new_reseed_value*) と*new_reseed_value*に非常に低い値を設定し、DBCC CHECKIDENT を実行 (*table_name*、RESEED) 値を修正します。|  
|すべての行がテーブルから削除されている。|DBCC checkident (*table_name*、RESEED,*new_reseed_value*) と*new_reseed_value*開始値に設定します。|  
  
## <a name="changing-the-seed-value"></a>シード値の変更  
 シード値は、テーブルに読み込まれる最初の行の ID 列に挿入される値です。 以降の行にはすべて、現在の ID 値 (テーブルまたはビューに対して生成された最後の ID 値) に増分値を加えた値が格納されます。  
  
 DBCC CHECKIDENT を使用して、次のタスクを実行することはできません。  
  
-   テーブルまたはビューの作成時に ID 列に指定された、元のシード値を変更する。  
  
-   テーブルまたはビュー内の既存の行にシード値を再生成する。  
  
 元のシード値を変更したり任意の既存の行にシード値を再生成したりするには、ID 列を削除し、新しいシード値を指定して作り直す必要があります。 テーブルにデータが含まれている場合、ID 番号が、指定のシード値および増分値を使用して既存の行に追加されます。 行の更新順序は保証されません。  
  
## <a name="result-sets"></a>結果セット  
 ID 列を含むテーブルに対してオプションが指定されているかどうかにかかわらず、DBCC CHECKIDENT は、新しいシード値の指定以外のすべての操作に対して次のメッセージを返します。  
  
`Checking identity information: current identity value '\<current identity value>', current column value '\<current column value>'. DBCC execution completed. If DBCC printed error messages, contact your system administrator.`
  
 再シードを使用して新しいシード値を指定して DBCC CHECKIDENT を使用する場合*new_reseed_value*、次のメッセージが返されます。  
  
`Checking identity information: current identity value '\<current identity value>'. DBCC execution completed. If DBCC printed error messages, contact your system administrator.`
  
## <a name="permissions"></a>権限  
 呼び出し元のテーブルを含むスキーマを所有またはのメンバーである必要があります、 **sysadmin**固定サーバー ロール、 **db_owner**固定データベース ロール、または**db_ddladmin**固定データベース ロール。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-resetting-the-current-identity-value-if-it-is-needed"></a>A. 必要に応じて現在の ID 値をリセットする  
 次の例は、指定されたテーブルでの必要な場合に現在の id 値をリセット、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。  
  
```  
USE AdventureWorks2012;  
GO  
DBCC CHECKIDENT ('Person.AddressType');  
GO  
```  
  
### <a name="b-reporting-the-current-identity-value"></a>B. 現在の ID 値を報告する  
 次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース内の指定されたテーブルの現在の ID 値を報告します。ID 値が正しくない場合でも、ID 値の修正は行いません。  
  
```  
USE AdventureWorks2012;   
GO  
DBCC CHECKIDENT ('Person.AddressType', NORESEED);   
GO  
  
```  
  
### <a name="c-forcing-the-current-identity-value-to-a-new-value"></a>C. 現在の ID 値を強制的に新しい値に設定する  
 次の例では、現在の id 値を強制する、`AddressTypeID`内の列、`AddressType`テーブル 10 の値にします。 テーブルには既存の行があるため、次に挿入される行では値に 11 が使用されます。この値は、列の値に対して定義されている新しい現在の増分値に 1 を加えた値です。  
  
```  
USE AdventureWorks2012;  
GO  
DBCC CHECKIDENT ('Person.AddressType', RESEED, 10);  
GO  
  
```  
  
## <a name="see-also"></a>参照  
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[IDENTITY &#40;Property&#41; &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql-identity-property.md)  
[ID 列のレプリケート](../../relational-databases/replication/publish/replicate-identity-columns.md)  
[USE &#40;Transact-SQL&#41;](../../t-sql/language-elements/use-transact-sql.md)  
[IDENT_SEED &#40;Transact-SQL&#41;](../../t-sql/functions/ident-seed-transact-sql.md)  
[IDENT_INCR &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/ident-incr-transact-sql.md)  
  
  
