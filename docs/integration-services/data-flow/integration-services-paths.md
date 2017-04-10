---
title: "Integration Services のパス | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.patheditor.general.f1"
  - "sql13.dts.designer.patheditor.metadata.f1"
  - "sql13.dts.designer.patheditor.visualizers.f1"
helpviewer_keywords: 
  - "パス [Integration Services], パスについて"
  - "データ フロー [Integration Services], パス"
  - "パス [Integration Services]"
  - "連結先 [Integration Services], パス"
  - "連結元 [Integration Services], パス"
ms.assetid: 6c4629a9-2ede-4011-9101-3b342249640e
caps.latest.revision: 41
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# Integration Services のパス
  パスは、データ フロー コンポーネントの出力を別のコンポーネントの入力に連結することにより、データ フロー内の 2 つのコンポーネントを連結します。 パスには連結元と連結先があります。 たとえば、パスが OLE DB ソースと並べ替え変換を連結する場合、OLE DB ソースはパスの連結元であり、並べ替え変換はパスの連結先になります。 連結元とはパスが開始するコンポーネントで、連結先とはパスが終了するコンポーネントのことです。  
  
 パッケージを [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで実行する場合、データ ビューアーをパスにアタッチすることにより、データ フロー内のデータを表示できます。 データ ビューアーを構成し、グリッドにデータを表示できます。 データ ビューアーは、デバッグ用のツールとして便利です。 詳細については、「[データ フローのデバッグ](../../integration-services/troubleshooting/debugging-data-flow.md)」を参照してください。  
  
## パスの構成  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでは **[データ フロー パス エディター]** ダイアログ ボックスが用意され、これを使用すると、パスのプロパティの設定、パスに渡されるデータ列のメタデータの表示、およびデータ ビューアーの構成を行うことができます。  
  
 構成可能なパスのプロパティは、パスの名前、説明、および注釈です。 パスはプログラムによって構成することもできます。 詳細については、「[プログラムによるデータ フロー コンポーネントの接続](../../integration-services/building-packages-programmatically/connecting-data-flow-components-programmatically.md)」を参照してください。  
  
 パスの注釈を設定すると、[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーの **[データ フロー]** タブにあるデザイン画面に、パスの連結元の名前またはパスの名前が表示されます。 パスの注釈は、データ フロー、制御フロー、およびイベント ハンドラーに追加できる注釈と同様です。 唯一の違いは、パスの注釈はパスにアタッチされるのに対し、他の注釈は、[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーの **[データ フロー]**、**[制御フロー]**、および **[イベント ハンドラー]** タブに表示される点です。  
  
 パスの注釈のメタデータは、各列の名前、データ型、有効桁数、小数点以下桁数、長さ、コード ページ、およびソース コンポーネントを、直前のコンポーネントの出力内で表示します。 ソース コンポーネントとは、列を作成したデータ フロー コンポーネントのことです。 このコンポーネントは、データ フロー内で最初のコンポーネントである場合もあれば、そうでない場合もあります。 たとえば、全体結合変換と並べ替え変換では独自の列が作成され、その列が出力列のソースになります。 対照的に、列コピー変換では、列を変更しないまま渡したり、入力列をコピーして新しい列を作成できます。 列コピー変換は、新しい列に対してのみ変換元コンポーネントとなります。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[データ フロー パス エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[データ フロー パス エディター] ([全般] ページ)](../Topic/Data%20Flow%20Path%20Editor%20\(General%20Page\).md)  
  
-   [[データ フロー パス エディター] ([メタデータ] ページ)](../Topic/Data%20Flow%20Path%20Editor%20\(Metadata%20Page\).md)  
  
-   [[データ フロー パス エディター] ([データ ビューアー] ページ)](../Topic/Data%20Flow%20Path%20Editor%20\(Data%20Viewers%20Page\).md)  
  
 プログラムによって設定できるプロパティの詳細については、「[パスのプロパティ](../Topic/Path%20Properties.md)」を参照してください。  
  
## 関連タスク  
  
-   [データ フロー パス エディターでパスのメタデータを表示する](../Topic/View%20Path%20Metadata%20in%20the%20Data%20Flow%20Path%20Editor.md)  
  
-   [データ フロー内でコンポーネントを連結する](../../integration-services/data-flow/connect-components-in-a-data-flow.md)  
  
## 参照  
 [データ フロー](../../integration-services/data-flow/data-flow.md)  
  
  