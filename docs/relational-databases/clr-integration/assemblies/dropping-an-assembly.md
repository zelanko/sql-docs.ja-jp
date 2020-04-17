---
title: アセンブリを削除する |マイクロソフトドキュメント
description: 不要になったアセンブリは、SQL Server のアセンブリを削除または削除できます。 DROP ASSEMBLY を使用して、アセンブリと関連ファイルを削除します。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- removing assemblies
- DROP ASSEMBLY statement
- assemblies [CLR integration], removing
- dropping assemblies
ms.assetid: 03481034-dc91-4488-ab24-ba44243e2690
author: rothja
ms.author: jroth
ms.openlocfilehash: 48fca2d5a255193800fed39e9869e1be231229a9
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81485621"
---
# <a name="dropping-an-assembly"></a>アセンブリの削除
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  CREATE ASSEMBLY ステートメントを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に登録された各アセンブリは、そのアセンブリで提供される機能が不要になれば削除できます。 アセンブリを削除すると、アセンブリと、デバッグ ファイルなどこれに関連するファイルがすべて、データベースから削除されます。 アセンブリを削除するには、DROP ASSEMBLY ステートメントを次の構文で使用します。  
  
```  
DROP ASSEMBLY MyDotNETAssembly  
```  
  
 DROP ASSEMBLY は、現在実行中のアセンブリを参照するコードに影響を与えることはありませんが、DROP ASSEMBLY を実行後は、アセンブリ コードを起動しようとすると失敗します。  
  
 アセンブリがデータベースに存在する別のアセンブリにより参照されている場合、または、アセンブリが現在のデータベースで共通言語ランタイム (CLR) 関数、プロシージャ、トリガー、ユーザー定義型 (UDT)、ユーザー定義集計 (UDA) により使用されている場合、DROP ASSEMBLY はエラーを返します。 まず、DROP AGGREGATE、DROP FUNCTION、DROP PROCEDURE、DROP TRIGGER、および DROP TYPE ステートメントを使用して、アセンブリに含まれるすべてのマネージド データベース オブジェクトを削除します。  
  
## <a name="removing-a-udt-from-the-database"></a>データベースからの UDT の削除  
 DROP TYPE ステートメントを使用すると、現在のデータベースから UDT が削除されます。 UDT を削除すると、DROP ASSEMBLY ステートメントを使用してデータベースからアセンブリを削除できます。  
  
 次の状況のように、オブジェクトが UDT に依存している場合、DROP TYPE ステートメントは失敗します。  
  
-   UDT を使用して定義した列を含むデータベース内のテーブル。  
  
-   WITH SCHEMABINDING 句を使用してデータベースに作成した UDT の変数またはパラメーターを使用する関数、ストアド プロシージャ、またはトリガー。  
  
### <a name="finding-udt-dependencies"></a>UDT 依存関係の検出  
 最初にすべての依存オブジェクトを削除してから、DROP TYPE ステートメントを実行する必要があります。 次[!INCLUDE[tsql](../../../includes/tsql-md.md)]のクエリは **、AdventureWorks**データベース内の UDT を使用するすべての列とパラメーターを検索します。  
  
```  
USE Adventureworks;  
SELECT o.name AS major_name, o.type_desc AS major_type_desc  
     , c.name AS minor_name, c.type_desc AS minor_type_desc  
     , at.assembly_class  
  FROM (  
        SELECT object_id, name, user_type_id, 'SQL_COLUMN' AS type_desc  
          FROM sys.columns  
     UNION ALL  
        SELECT object_id, name, user_type_id, 'SQL_PROCEDURE_PARAMETER'  
          FROM sys.parameters  
     ) AS c  
  JOIN sys.objects AS o  
    ON o.object_id = c.object_id  
  JOIN sys.assembly_types AS at  
    ON at.user_type_id = c.user_type_id;   
```  
  
## <a name="see-also"></a>参照  
 [CLR 統合アセンブリの管理](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)   
 [アセンブリの変更](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)   
 [アセンブリの作成](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)   
 [トランザクション SQL&#41;&#40;集約を削除する](../../../t-sql/statements/drop-aggregate-transact-sql.md)   
 [トランザクション SQL&#41;&#40;ドロップ関数](../../../t-sql/statements/drop-function-transact-sql.md)   
 [トランザクション SQL&#41;&#40;ドロップ プロシージャ](../../../t-sql/statements/drop-procedure-transact-sql.md)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-trigger-transact-sql.md)   
 [DROP TYPE &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-type-transact-sql.md)  
  
  
