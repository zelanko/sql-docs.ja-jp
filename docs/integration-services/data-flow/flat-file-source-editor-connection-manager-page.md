---
title: "[フラット ファイル ソース エディター] ([接続マネージャー] ページ) | Microsoft Docs"
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
  - "sql13.dts.designer.flatfilesourceadapter.connection.f1"
helpviewer_keywords: 
  - "フラット ファイル ソース エディター"
ms.assetid: 2efd6baa-ed75-4f3f-b667-514024cebdb8
caps.latest.revision: 29
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 29
---
# [フラット ファイル ソース エディター] ([接続マネージャー] ページ)
  **[フラット ファイル ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、フラット ファイル ソースが使用する接続マネージャーを選択できます。 フラット ファイル ソースは、区切り形式、固定幅形式、または区切りと固定幅が混在した形式のテキスト ファイルからデータを読み取ります。  
  
 フラット ファイル ソースは、次のいずれかの種類の接続マネージャーを使用できます。  
  
-   ソースが単一のフラット ファイルの場合は、フラット ファイル接続マネージャー。 詳しくは「[フラット ファイル接続マネージャー](../../integration-services/connection-manager/flat-file-connection-manager.md)」をご覧ください。  
  
-   ソースが複数フラット ファイルで、データ フロー タスクが For ループ コンテナーなどのループ コンテナーの内部にある場合は、複数フラット ファイル接続マネージャー。 コンテナーの各ループで、フラット ファイル ソースは、複数フラット ファイル接続マネージャーが提供する次のファイル名からデータを読み込みます。 詳細については、「[複数フラット ファイル接続マネージャー](../../integration-services/connection-manager/multiple-flat-files-connection-manager.md)」を参照してください。  
  
 フラット ファイル ソースの詳細については、「 [Flat File Source](../../integration-services/data-flow/flat-file-source.md)」を参照してください。  
  
## オプション  
 **[フラット ファイル接続マネージャー]**  
 既存の接続マネージャーを一覧から選択するか、**[新規作成]** をクリックして新しい接続マネージャーを作成します。  
  
 **新規**  
 新しい接続マネージャーを作成するには、**[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスを使用します。  
  
 **[データ ソースの NULL 値をデータ フローで NULL 値として保持する]**  
 データが抽出されたときに NULL 値を保持するかどうかを指定します。 このプロパティの既定値は **false** です。 この値が **false** である場合、フラット ファイル変換元は変換元データの NULL 値を各列の適切な既定値で置き換えます。たとえば、文字列型の列の場合は空の文字列、数値型の列の場合は 0 です。  
  
 **プレビュー**  
 **[データ ビュー]** ダイアログ ボックスを使用して、結果をプレビューします。 プレビューでは、最大で 200 行を表示できます。  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [フラット ファイル ソース エディター ([列] ページ)](../Topic/Flat%20File%20Source%20Editor%20\(Columns%20Page\).md)   
 [フラット ファイル ソース エディター ([エラー出力] ページ)](../Topic/Flat%20File%20Source%20Editor%20\(Error%20Output%20Page\).md)   
 [フラット ファイル接続マネージャー](../../integration-services/connection-manager/flat-file-connection-manager.md)  
  
  