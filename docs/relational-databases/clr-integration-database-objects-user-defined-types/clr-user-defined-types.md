---
title: "CLR ユーザー定義型 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- validation [CLR integration]
- types [CLR integration]
- UserDefined serialization format [CLR integration]
- null values [CLR integration]
- serialization
- Native serialization format [CLR integration]
- databases [CLR integration]
- building database objects [CLR integration], user-defined types
- user-defined types [CLR integration]
- common language runtime [SQL Server], user-defined types
- UDTs [CLR integration]
- database objects [CLR integration], user-defined types
- turning on CLR functionality
- customizing UDT expression return types [CLR integration]
- UDTs [CLR integration], about UDTs
- comparing UDT values
- annotations [CLR integration]
- user-defined types [CLR integration], about UDTs
- variables [CLR integration]
- invoking UDT methods
- indexes [CLR integration]
ms.assetid: 27c4889b-c543-47a8-a630-ad06804f92df
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 79f5a6c9c827d3502cf7c636ffb5e49bd16f0b13
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="clr-user-defined-types"></a>CLR ユーザー定義型
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、.NET Framework CLR (共通言語ランタイム) で作成されているアセンブリでプログラミングしたデータベース オブジェクトを作成できます。 CLR で用意された豊富なプログラミング モデルを使用できるデータベース オブジェクトには、トリガー、ストアド プロシージャ、関数、集計関数、型などがあります。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、CLR コードを実行する機能が既定で無効になっています。 使用して CLR を有効にすることができます、 **sp_configure**システム ストアド プロシージャです。  
  
 以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]で CLR オブジェクトのストレージを有効にすると、サーバーのスカラー型システムを拡張するユーザー定義型 (Udt) を使用することができます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。 1 つの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム データ型で構成される従来の別名データ型とは異なり、UDT には複数の要素や複数の動作を含めることができます。  
  
 UDT はシステム全体からアクセスされるので、UDT を複合データ型に使用すると、パフォーマンスに悪影響を与えることがあります。 通常、複合データは従来の行やテーブルを使用する場合に最適になるようにモデル化されています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の UDT は、次のような場合に適しています。  
  
-   日付型、時刻型、通貨型、および拡張数値型  
  
-   地理空間アプリケーション  
  
-   エンコードされたデータまたは暗号化されたデータ  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で UDT を開発する処理は、次の手順から構成されています。  
  
1.  **コードおよび UDT を定義するアセンブリをビルドします。** UDT は、検証可能なコードを生成する .NET Framework 共通言語ランタイム (CLR) でサポートされる任意の言語を使用して定義されます。 このような言語には、Visual C# や Visual Basic .NET があります。 データは、.NET Framework のクラスまたは構造体のフィールドやプロパティとして公開され、動作はクラスまたは構造体のメソッドによって定義されます。  
  
2.  **アセンブリを登録します。** UDT は、Visual Studio のユーザー インターフェイスを使用してデータベース プロジェクトに配置することも、[!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY ステートメントを使用して、クラスまたは構造体を含むアセンブリをデータベースにコピーすることもできます。  
  
3.  **SQL Server で UDT を作成します。** アセンブリがホスト データベースに読み込まれた後、[!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE ステートメントを使用して UDT を作成し、UDT のメンバーとしてクラスまたは構造体のメンバーを公開します。 UDT は 1 つのデータベースのコンテキストにのみ存在します。UDT はいったん登録されると、作成時のベースとなっていた外部ファイルに対する依存関係がなくなります。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] より前のバージョンでは、.NET Framework アセンブリから作成された UDT がサポートされていませんでした。 ただし、引き続き使用できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]別名データ型を使用して**sp_addtype**です。 CREATE TYPE 構文を使用すると、ネイティブの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザー定義データ型と UDT の両方を作成できます。  
  
4.  **テーブル、変数、または UDT を使用してパラメーターを作成する**で始まる[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、ユーザー定義型の変数として、テーブルの列の定義として使用できます、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチ、またはの引数として、[!INCLUDE[tsql](../../includes/tsql-md.md)]関数またはストアドプロシージャです。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ユーザー定義型を作成します。](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
 UDT の作成方法について説明します。  
  
 [SQL Server でのユーザー定義型の登録](../../relational-databases/clr-integration-database-objects-user-defined-types/registering-user-defined-types-in-sql-server.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] での UDT の登録方法と管理方法について説明します。  
  
 [SQL Server のユーザー定義型の使用](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)  
 UDT を使用してクエリを作成する方法について説明します。  
  
 [ADO.NET でのユーザー定義型へのアクセス](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-in-ado-net.md)  
 ADO.NET の .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して UDT を操作する方法について説明します。  
  
  
