---
title: "列インポート変換 | Microsoft Docs"
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
  - "sql13.dts.designer.importcolumntrans.f1"
helpviewer_keywords: 
  - "列インポート変換 [Integration Services]"
  - "列 [Integration Services]、インポート"
  - "データのインポート、SSIS パッケージ"
  - "挿入、データ"
ms.assetid: ac3b74c1-ef54-4297-8062-1734324fffcc
caps.latest.revision: 44
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 44
---
# 列インポート変換
  列インポート変換は、ファイルのデータを読み取り、そのデータをデータ フローの列に追加します。 この変換を使用すると、パッケージは、別々のファイルに格納されているテキストや画像を 1 つのデータ フローに追加できます。 たとえば、製品情報を保存するテーブルにデータを読み込むデータ フローに列インポート変換を含めると、各製品に対する顧客評価をファイルからインポートし、データ フローに追加できます。  
  
 列インポート変換は、次の方法で構成できます。  
  
-   データを追加する列を指定します。  
  
-   バイト順マーク (BOM) が必要かどうかを指定します。  
  
    > [!NOTE]  
    >  BOM が必要になるのは、データが DT_NTEXT データ型の場合だけです。  
  
 変換入力の列には、データを保持するファイル名が含まれます。 データセットの各行には、異なるファイルを指定できます。 列インポート変換が行を処理すると、ファイル名を読み取り、ファイル システム内の対応するファイルを開き、ファイルの内容を出力列に読み込みます。 出力列のデータ型は、DT_TEXT、DT_NTEXT、または DT_IMAGE 型である必要があります。 詳細については、「 [Integration Services Data Types](../../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
 この変換は、1 つの入力、1 つの出力、および 1 つのエラー出力をとります。  
  
## 列インポート変換の構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](../Topic/Common%20Properties.md)  
  
-   [変換のカスタム プロパティ](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
## 関連タスク  
 このコンポーネントのプロパティの設定方法の詳細については、「[データ フロー コンポーネントのプロパティを設定する](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
## 参照  
 [列エクスポート変換](../../../integration-services/data-flow/transformations/export-column-transformation.md)   
 [データ フロー](../../../integration-services/data-flow/data-flow.md)   
 [Integration Services の変換](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  