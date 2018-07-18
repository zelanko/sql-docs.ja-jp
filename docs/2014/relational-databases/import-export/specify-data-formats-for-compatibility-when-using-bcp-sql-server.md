---
title: bcp を使用した互換性のためのデータ形式の指定 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: data-movement
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- bulk exporting [SQL Server], compatibility
- bulk importing [SQL Server], compatibility
- compatibility [SQL Server], data formats
- data formats [SQL Server], compatibility
- bcp utility [SQL Server], compatibility
ms.assetid: cd5fc8c8-eab1-4165-9468-384f31e53f0a
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 42266e1f4ab136045c16d1e0f41d6ae802c3f1c7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37154543"
---
# <a name="specify-data-formats-for-compatibility-when-using-bcp-sql-server"></a>bcp を使用した互換性のためのデータ形式の指定 (SQL Server)
  このトピックでは、データ形式属性、フィールド固有のプロンプト、および xml 以外のフォーマット ファイルでフィールドのデータの格納について説明します、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `bcp`コマンド。 このトピックの内容は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データを一括エクポートして別のプログラム (別のデータベース プログラムなど) に一括インポートする場合に有用です。 ソース テーブルの既定のデータ形式 (ネイティブ、文字、または Unicode) が、他のプログラムで想定されているデータ レイアウトと互換性がない場合があります。互換性がない場合はデータをエクスポートするときに、データ レイアウトを記述する必要があります。  
  
> [!NOTE]  
>  データをインポートまたはエクスポートするためのデータ形式に精通していない場合は、「 [一括インポートまたは一括エクスポートのデータ形式 &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md)」を参照してください。  
  
 **このトピックの内容**  
  
-   [bcp データ形式属性](#bcpDataFormatAttr)  
  
-   [フィールド固有のプロンプトの概要](#FieldSpecificPrompts)  
  
-   [XML 以外のフォーマット ファイル フィールドのデータの格納](#FieldByFieldNonXmlFF)  
  
-   [関連タスク](#RelatedTasks)  
  
##  <a name="bcpDataFormatAttr"></a> bcp データ形式の属性  
 `bcp` コマンドにより、次のデータ形式属性に関して、データ ファイル内の各フィールドの構造を指定できます。  
  
-   ファイル ストレージ型  
  
     *ファイル ストレージ型* は、データ ファイルへのデータの格納方法を記述します。 データとしてエクスポートできますデータ ファイルに、データベース テーブルの型 (ネイティブ形式)、文字表現 (文字形式)、または任意のデータ型を暗黙的な変換がサポートされています。たとえば、コピー、`smallint`として、`int`します。 ユーザー定義のデータ型は、基本データ型としてエクスポートされます。 詳細については、「 [bcp を使用したファイル ストレージ型の指定 &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)」を参照してください。  
  
-   プレフィックス長  
  
     `bcp` コマンドでは、ネイティブ形式のデータをデータ ファイルに一括エクスポートするためのファイル ストレージが最も少なくなるように、各フィールドの前にそのフィールドの長さを 1 文字以上の文字列で指定します。 このような文字列を、 *プレフィックス長文字列*と呼びます。 詳細については、「 [bcp を使用したデータ ファイルのプレフィックス長の指定 &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)」を参照してください。  
  
-   フィールド長  
  
     フィールド長は、文字形式でデータを表現するために必要な文字の最大数を示します。 データがネイティブ形式で格納される場合、フィールド長は既にわかっています。 詳細については、「 [bcp を使用したフィールド長の指定 &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md)」を参照してください。  
  
-   フィールド ターミネータ  
  
     文字列データ フィールドでは、省略可能なターミネータ文字を使用して、データ ファイルの各フィールドの末尾 ( *フィールド ターミネータ*を使用) と各行の末尾 ( *行ターミネータ*を使用) を示すことができます。 ターミネータ文字は、フィールドや行の終了位置と次のフィールドや行の開始位置を、データ ファイルを読み取るプログラムに示す方法の 1 つです。 詳細については、「 [フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)」を参照してください。  
  
##  <a name="FieldSpecificPrompts"></a> フィールド固有のプロンプトの概要  
 対話型`bcp`コマンドが含まれています、**で**または**アウト**オプションしますが、フォーマット ファイル スイッチも含まれていません (**-f**) またはデータ形式スイッチ (**-n**、 **-c**、 **-w**、または **-n**) を上記の各ソースまたはターゲット テーブルの各列では、コマンド プロンプト属性を有効にします。 各プロンプトで、`bcp`コマンドに基づいて既定値が提供、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル列のデータ型。 すべての問い合わせに対して既定値を受け入れることは、コマンド ラインでネイティブ形式 (**-n**) を指定するのと同じ結果になります。 各プロンプトには、[*default*] のように既定値が角かっこ付きで表示されます。 表示される既定値を受け入れるには、Enter キーを押します。 既定値以外を指定するには、プロンプトで新しい値を入力します。  
  
### <a name="example"></a>例  
 次の例では、`bcp`コマンドに一括データのエクスポート、`HumanResources.myTeam`に対話形式でテーブル、`myTeam.txt`ファイル。 このテーブルを作成しないと、例を実行できません。 テーブルの詳細とテーブルを作成する方法については、「[HumanResources.myTeam サンプル テーブル &#40;SQL Server&#41;](humanresources-myteam-sample-table-sql-server.md)」を参照してください。  
  
 コマンドは、フォーマット ファイルでも、データ型を指定します。 原因`bcp`データ形式情報を要求します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows コマンド プロンプトで、次のように入力します。  
  
```  
bcp AdventureWorks.HumanResources.myTeam out myTeam.txt -T  
```  
  
 列ごとに、bcp からフィールド固有の値が要求されます。 次の例は、テーブルの `EmployeeID` 列と `Name` 列のフィールド固有のプロンプトを示しています。また、各列の既定のファイル保存形式 (ネイティブ形式) も示しています。 `EmployeeID` 列と `Name` 列のプレフィックス長は、それぞれ 0 と 2 です。 ここでは、各フィールドのターミネータとして、ユーザーがコンマ (`,`) を指定します。  
  
 `Enter the file storage type of field EmployeeID [smallint]:`  
  
 `Enter prefix-length of field EmployeeID [0]:`  
  
 `Enter field terminator [none]:,`  
  
 `Enter the file storage type of field Name [nvarchar]:`  
  
 `Enter prefix length of field Name [2]:`  
  
 `Enter field terminator [none]:,`  
  
 `.`  
  
 `.`  
  
 `.`  
  
 テーブルの列ごとに、列の順番に従って、同等のプロンプトが (必要に応じて) 表示されます。  
  
##  <a name="FieldByFieldNonXmlFF"></a> XML 以外のフォーマット ファイルでのフィールドごとのデータの格納  
 結局のところ、テーブルの列を指定する、`bcp`コマンドでは、必要に応じて、フィールドの情報指定した (前の例を参照) を格納する XML 以外のフォーマット ファイルを生成するように求められます。 フォーマット ファイルを生成することを選択すると、いつでも、そのテーブルからデータをエクスポートしたり、同じような構造のデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にインポートできます。  
  
> [!NOTE]  
>  フォーマット ファイルを使用して、データ ファイルから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにデータを一括インポートできます。また、形式を再度指定しないで、そのテーブルからデータを一括エクスポートできます。 詳細については、「 [データのインポートまたはエクスポート用のフォーマット ファイル &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)」を参照してください。  
  
 次の例では、`myFormatFile.fmt` という名前の XML 以外のフォーマット ファイルを作成します。  
  
 `Do you want to save this format information in a file? [Y/n] y`  
  
 `Host filename: [bcp.fmt]myFormatFile.fmt`  
  
 フォーマット ファイルの既定の名前は bcp.fmt ですが、必要に応じて別のファイル名を指定できます。  
  
> [!NOTE]  
>  文字形式やネイティブ形式など、ファイル保存形式に 1 つのデータ形式を使用するデータ ファイルの場合は、 **format** オプションを使用することで、データをエクスポートまたはインポートしなくても、フォーマット ファイルをすばやく作成できます。 この方法は簡単で、XML フォーマット ファイルと XML 以外のフォーマット ファイルのどちらも作成できるという利点があります。 詳細については、「[フォーマット ファイルの作成 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)」をご覧ください。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [bcp を使用したファイル ストレージ型の指定 &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
-   [bcp を使用したデータ ファイルのプレフィックス長の指定 &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
-   [bcp を使用したフィールド長の指定 &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md)  
  
-   [フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)  
  
## <a name="related-content"></a>関連コンテンツ  
 [なし] :  
  
## <a name="see-also"></a>参照  
 [データの一括インポートと一括エクスポート &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md)   
 [一括インポートまたは一括エクスポートのデータ形式 &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md)   
 [bcp ユーティリティ](../../tools/bcp-utility.md)   
 [データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
