---
title: "フラット ファイル変換先 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.flatfiledest.f1"
helpviewer_keywords: 
  - "フラット ファイル"
  - "フラット ファイル変換先"
  - "テキスト ファイルの書き込み [Integration Services]"
  - "変換先 [Integration Services], フラット ファイル"
ms.assetid: e0d6e356-8db4-48aa-ba66-029397f98f61
caps.latest.revision: 49
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 49
---
# フラット ファイル変換先
  フラット ファイル変換先は、データをテキスト ファイルに書き込みます。 テキスト ファイルには、区切り形式、固定幅形式、行区切り記号を使用した固定幅形式、または幅合わせしない形式を使用できます。  
  
 フラット ファイル変換先は、次の方法で構成できます。  
  
-   データが書き込まれる前にファイルに挿入される、テキストのブロックを指定します。 このテキストには、列見出しなどの情報を設定できます。  
  
-   同じ名前の変換先ファイルにあるデータを上書きするかどうかを指定します。  
  
 この変換先では、フラット ファイル接続マネージャーを使用してテキスト ファイルにアクセスします。 フラット ファイル変換先が使用するフラット ファイル接続マネージャーでプロパティを設定することにより、フラット ファイル変換先がテキスト ファイルをフォーマットする方法と書き込む方法を指定できます。 フラット ファイル接続マネージャーを構成する際には、ファイルおよびファイル内の各列に関する情報を指定できます。 たとえば、ファイルの列と行を区切る文字や、各列のデータ型や長さを指定できます。 詳しくは、「[フラット ファイル接続マネージャー](../../integration-services/connection-manager/flat-file-connection-manager.md)」をご覧ください。  
  
 フラット ファイル変換先には、Header カスタム プロパティがあります。 このプロパティは、パッケージの読み込み時にプロパティ式で更新できます。 詳しくは、「[Integration Services &#40;SSIS&#41; の式](../../integration-services/expressions/integration-services-ssis-expressions.md)」、「[パッケージでプロパティ式を使用する](../../integration-services/expressions/use-property-expressions-in-packages.md)」、および「[フラット ファイルのカスタム プロパティ](../../integration-services/data-flow/flat-file-custom-properties.md)」をご覧ください。  
  
 この変換先は 1 つの出力をとります。 エラー出力はサポートされていません。  
  
## フラット ファイル変換先の構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[フラット ファイル ソース エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[フラット ファイル変換先エディター] &#40;[接続マネージャー] ページ&#41;](../Topic/Flat%20File%20Destination%20Editor%20\(Connection%20Manager%20Page\).md)  
  
-   [[フラット ファイル変換先エディター] &#40;[マッピング] ページ&#41;](../Topic/Flat%20File%20Destination%20Editor%20\(Mappings%20Page\).md)  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](../Topic/Common%20Properties.md)  
  
-   [フラット ファイルのカスタム プロパティ](../../integration-services/data-flow/flat-file-custom-properties.md)  
  
## 関連タスク  
 データ フロー コンポーネントのプロパティの設定方法の詳細については、「[データ フロー コンポーネントのプロパティを設定する](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)」をご覧ください。  
  
## 参照  
 [フラット ファイル ソース](../../integration-services/data-flow/flat-file-source.md)   
 [データ フロー](../../integration-services/data-flow/data-flow.md)  
  
  