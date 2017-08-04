---
title: "Excel 接続マネージャー |Microsoft ドキュメント"
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- files [Integration Services], connections
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: 667419f2-74fb-4b50-b963-9197d1368cda
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c817f552e527f0d01ec7638eb5f605da572cf9c0
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="excel-connection-manager"></a>Excel 接続マネージャー
  Excel 接続マネージャーを使用すると、パッケージは既存の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel ブック ファイルに接続できます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に含まれる Excel ソースと Excel 変換先は、Excel 接続マネージャーを使用します。  
  
 Excel 接続マネージャーをパッケージに追加するときに、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] により、実行時に Excel 接続として解決される接続マネージャーを作成し、接続マネージャーのプロパティを設定して、接続マネージャーをパッケージの **Connections** コレクションに追加します。  
  
 接続マネージャーの **ConnectionManagerType** プロパティは、 **EXCEL**に設定されます。  
  
## <a name="configuration-of-the-excel-connection-manager"></a>Excel 接続マネージャーの構成  
 Excel 接続マネージャーは、次の方法で構成できます。  
  
-   Excel ブック ファイルのパスを指定します。  
  
    > [!NOTE]  
    >  パスワードで保護された Excel ファイルには接続できません。  
  
-   ファイルの作成に使用した Excel のバージョンを指定します。  
  
-   選択したワークシート内または範囲内でアクセスするデータの最初の行に、列名が格納されているかどうかを示します。  
  
 Excel ソースによって Excel 接続マネージャーが使用された場合は、抽出したデータに列名が含められます。 Excel 変換先によって使用された場合は、出力されたデータに列名が含められます。  
  
 Excel ソースおよび Excel 変換先の動作の詳細については、「 [Excel ソース](../../integration-services/data-flow/excel-source.md) 」および「 [Excel 変換先](../../integration-services/data-flow/excel-destination.md)」を参照してください。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [Excel 接続マネージャー](../../integration-services/connection-manager/excel-connection-manager-editor.md)」を参照してください。  
  
 プログラムによる接続マネージャーの構成の詳細については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」および「 [プログラムによる接続の追加](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)に設定されます。  
  
 Excel ファイルのグループによるループ処理については、「 [Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)」を参照してください。  
  
## <a name="related-tasks"></a>関連タスク  
  
-   [Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
-   [Excel ブックに接続する](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)  
  
  
