---
title: "Integration Services (SSIS) のクエリ | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.querybuilder.f1"
helpviewer_keywords: 
  - "クエリ ビルダー [Integration Services]"
  - "クエリ [Integration Services]"
  - "ステートメント [Integration Services]"
  - "クエリ [Integration Services], パッケージのクエリについて"
ms.assetid: 8822bd29-4575-46c8-92a0-1a39bc2604c1
caps.latest.revision: 58
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 57
---
# Integration Services (SSIS) のクエリ
  SQL 実行タスク、OLE DB ソース、OLE DB 変換先、および参照変換では、SQL クエリを使用できます。 SQL 実行タスクでは、SQL ステートメントによってデータベース オブジェクトとデータを作成、更新、および削除したり、ストアド プロシージャを実行したり、SELECT ステートメントを実行したりすることができます。 OLE DB ソースと参照変換の場合、通常 SQL ステートメントは SELECT ステートメントまたは EXEC ステートメントです。 EXEC ステートメントで最もよく実行するのは、結果セットを返すストアド プロシージャです。  
  
 クエリを解析して、有効かどうかを確認できます。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] への接続を使用するクエリを解析すると、クエリは解析後に実行されて、実行結果 (成功または失敗) が解析結果に割り当てられます。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 以外のデータへの接続をクエリで使用する場合、ステートメントは解析されるだけです。  
  
 SQL ステートメントを定義するには、デザイナーに直接入力するか、ステートメントを含むファイル接続または変数を指定します。  
  
## 直接入力 SQL  
 クエリ ビルダーは、SQL 実行タスク、OLE DB ソース、OLE DB 変換先、および参照変換のユーザー インターフェイスで使用できます。 クエリ ビルダーを使用すると次の利点があります。  
  
-   視覚的な作業、または SQL コマンドを使用した作業  
  
     クエリ ビルダーには、クエリを視覚的に構成するグラフィカル ペインと、クエリの SQL テキストを表示するテキスト ペインがあります。 グラフィカル ペインとテキスト ペインのどちらでも作業ができます。 これらの表示はクエリ ビルダーによって同期されるため、クエリのテキストとグラフィカルな表示は常に一致します。  
  
-   関係付けられたテーブルの結合  
  
     クエリに複数のテーブルを追加する場合、クエリ ビルダーでは自動的にテーブル間の関係を認識し、適切な結合コマンドを作成します。  
  
-   データベースのクエリまたは更新  
  
     クエリ ビルダーでは、Transact-SQL SELECT ステートメントを使用してデータを返すことができます。また、データベースのレコードの更新、追加、削除を行うクエリを作成できます。  
  
-   結果の即時の表示と変更  
  
     クエリを実行したり、グリッドのレコードセットを使用して、データベースのレコードのスクロールや編集ができます。  
  
 クエリ ビルダーの視覚的な作業で作成できるのは SELECT クエリだけですが、テキスト ペインには DELETE や UPDATE ステートメントなど他の種類の SQL ステートメントを入力できます。 入力した SQL ステートメントに合わせて、グラフィカル ペインも自動的に更新されます。  
  
 また、直接入力は、タスクやデータ フロー コンポーネントのダイアログ ボックス、またはプロパティ ウィンドウにクエリを入力しても行えます。  
  
 詳細については、「[クエリ ビルダー](../Topic/Query%20Builder.md)」を参照してください。  
  
## ファイルの SQL  
 SQL 実行タスクの SQL ステートメントを、別のファイルに格納しておくことも可能です。 たとえば、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のクエリ エディターのようなツールを使用してクエリを記述し、ファイルに保存して、パッケージを実行するときにファイルからクエリを読み込むことができます。 ファイルには、実行する SQL ステートメントとコメントのみを含めることができます。 ファイルに格納された SQL ステートメントを使用するには、ファイル名とファイルの場所を指定するファイル接続を用意する必要があります。 詳しくは「 [File Connection Manager](../integration-services/connection-manager/file-connection-manager.md)」をご覧ください。  
  
## 変数の SQL  
 SQL 実行タスクの SQL ステートメントのソースが変数の場合、クエリが格納されている変数の名前を指定します。 変数の Value プロパティにクエリのテキストを格納します。 変数の ValueType プロパティを文字列データ型に設定し、Value プロパティに SQL ステートメントを入力またはコピーします。 詳細については、「[Integration Services &#40;SSIS&#41; の変数](../integration-services/integration-services-ssis-variables.md)」および「[パッケージで変数を使用する](../Topic/Use%20Variables%20in%20Packages.md)」を参照してください。  
  
  