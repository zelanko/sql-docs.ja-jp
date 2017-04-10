---
title: "複数フラット ファイル接続マネージャー | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "複数フラット ファイル接続マネージャー"
  - "接続 [Integration Services], フラット ファイル"
  - "フラット ファイル"
  - "フラット ファイル接続 [Integration Services]"
  - "接続マネージャー [Integration Services], 複数フラット ファイル"
  - "複数フラット ファイル接続"
ms.assetid: 31fc3f7a-d323-44f5-a907-1fa3de66631a
caps.latest.revision: 41
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 41
---
# 複数フラット ファイル接続マネージャー
  複数フラット ファイル接続マネージャーを使用すると、パッケージで複数のフラット ファイルのデータにアクセスできます。 たとえば、データ フロー タスクが For ループ コンテナーなどのループ コンテナーの内部にある場合は、フラット ファイル ソースで複数フラット ファイル接続マネージャーを使用できます。 コンテナーの各ループで、フラット ファイル ソースは、複数フラット ファイル接続マネージャーが提供する次のファイル名からデータを読み込みます。  
  
 複数フラット ファイル接続マネージャーをパッケージに追加すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は、実行時に複数のフラット ファイルの接続を解決する接続マネージャーを作成し、複数フラット ファイル接続マネージャーのプロパティを設定して、複数フラット ファイル接続マネージャーをパッケージの **Connections** コレクションに追加します。  
  
 接続マネージャーの **ConnectionManagerType** プロパティは、**MULTIFLATFILE** に設定されます。  
  
 複数フラット ファイル接続マネージャーは、次の方法で構成できます。  
  
-   使用するファイル、ロケール、およびコード ページを指定します。 ロケールは、日付など、ロケール依存型のデータの解釈に使用されます。コード ページは、文字列データを Unicode に変換するために使用されます。  
  
-   ファイル形式を指定します。 区切られた形式、固定幅形式、または幅合わせしない形式が使用できます。  
  
-   ヘッダー行、データ行、および列の区切り記号を指定します。 列の区切り記号は、ファイル レベルで設定し、列レベルで上書きできます。  
  
-   ファイルの最初の行に列の名前が含まれるかどうかを示します。  
  
-   テキスト修飾子文字を指定します。 各列は、テキスト修飾子を認識するように構成できます。  
  
-   各列の名前、データ型、最大幅などのプロパティを設定します。  
  
 複数フラット ファイル接続マネージャーが複数のファイルを参照する場合、ファイルのパスをパイプ (|) 文字で区切ります。 この接続マネージャーの **ConnectionString** プロパティの形式は、次のとおりです。  
  
 \<*パス*>|\<*パス*>  
  
 複数のファイルを指定する場合、ワイルドカード文字を使用することもできます。 たとえば、C ドライブ内のすべてのテキスト ファイルを参照するには、**ConnectionString** プロパティの値を「C:\\*.txt」に設定します。  
  
 複数フラット ファイル接続マネージャーが複数のファイルを参照する場合、ファイルの形式はすべて同じである必要があります。  
  
 複数フラット ファイル接続マネージャーでは、文字列型の列の長さが既定で 50 文字に設定されています。 **[複数フラット ファイル接続マネージャー エディター]** ダイアログ ボックスでは、データが切り捨てられたり、列の幅が広くなりすぎないように、サンプル データを評価して、これらの列の長さを自動的に変更できます。 フラット ファイル ソースまたは変換で列の長さを変更しない限り、データ フローでの列の長さは一定です。 これらの列が幅の狭い変換先列にマップされると、ユーザー インターフェイスに警告が表示されます。また、実行時にデータの切り捨てによるエラーが発生する場合があります。 フラット ファイル接続マネージャー、フラット ファイル ソース、または変換では、変換先列に合うように列のサイズを変更できます。 出力列の長さを変更するには、**[詳細エディター]** ダイアログ ボックスの **[入力プロパティと出力プロパティ]** タブで、出力列の **Length** プロパティを設定します。  
  
 接続マネージャーを使用するフラット ファイル ソースを追加および構成した後に、複数フラット ファイル接続マネージャーで列の長さを変更しても、フラット ファイル ソースの出力列のサイズを手動で変更する必要はありません。 **[フラット ファイル ソース]** ダイアログ ボックスを開くと、列のメタデータを同期するためのオプションがフラット ファイル ソースによって提供されます。  
  
## 複数フラット ファイル接続マネージャーの構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[複数フラット ファイル接続マネージャー エディター] ([全般] ページ)](../Topic/Multiple%20Flat%20Files%20Connection%20Manager%20Editor%20\(General%20Page\).md)  
  
-   [[複数フラット ファイル接続マネージャー エディター] ([列] ページ)](../Topic/Multiple%20Flat%20Files%20Connection%20Manager%20Editor%20\(Columns%20Page\).md)  
  
-   [[複数フラット ファイル接続マネージャー エディター] ([詳細設定] ページ)](../Topic/Multiple%20Flat%20Files%20Connection%20Manager%20Editor%20\(Advanced%20Page\).md)  
  
-   [[複数フラット ファイル接続マネージャー エディター] ([プレビュー] ページ)](../Topic/Multiple%20Flat%20Files%20Connection%20Manager%20Editor%20\(Preview%20Page\).md)  
  
 プログラムによる接続マネージャーの構成の詳細については、「<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>」および「[プログラムによる接続の追加](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)」を参照してください。  
  
## 参照  
 [フラット ファイル ソース](../../integration-services/data-flow/flat-file-source.md)   
 [フラット ファイル変換先](../../integration-services/data-flow/flat-file-destination.md)   
 [Integration Services (SSIS) の接続](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  