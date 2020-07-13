---
title: Excel 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- files [Integration Services], connections
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: 667419f2-74fb-4b50-b963-9197d1368cda
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 08cc1263c5d16df9b078e583d1c1e311f3747703
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85438489"
---
# <a name="excel-connection-manager"></a>Excel 接続マネージャー
  Excel 接続マネージャーを使用すると、パッケージは既存の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel ブック ファイルに接続できます。 Excel ソースおよび excel 変換先には、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] excel 接続マネージャーが使用されます。  
  
 Excel 接続マネージャーをパッケージに追加するときに、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] により、実行時に Excel 接続として解決される接続マネージャーを作成し、接続マネージャーのプロパティを設定して、接続マネージャーをパッケージの `Connections` コレクションに追加します。  
  
 接続マネージャーの `ConnectionManagerType` プロパティは、`EXCEL` に設定されます。  
  
> [!NOTE]  
>  パスワードで保護された Excel ファイルには接続できません。  
  
## <a name="configuration-of-the-excel-connection-manager"></a>Excel 接続マネージャーの構成  
 Excel 接続マネージャーは、次の方法で構成できます。  
  
-   Excel ブック ファイルのパスを指定します。  
  
-   ファイルの作成に使用した Excel のバージョンを指定します。  
  
-   選択したワークシート内または範囲内でアクセスするデータの最初の行に、列名が格納されているかどうかを示します。  
  
 Excel ソースによって Excel 接続マネージャーが使用された場合は、抽出したデータに列名が含められます。 Excel 変換先によって使用された場合は、出力されたデータに列名が含められます。  
  
 Excel 接続マネージャーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet 4.0 用の OLE DB プロバイダーと、それをサポートする EXCEL ISAM (インデックス付きシーケンシャルアクセス方式) ドライバーを使用して、excel データソースへの接続とデータの読み書きを行います。 Excel ソースおよび excel 変換先で使用する場合のこのプロバイダーとドライバーの動作の詳細については、「 [Excel ソース](../data-flow/excel-source.md)および Excel[変換先](../data-flow/excel-destination.md)」を参照してください。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [Excel 接続マネージャー](../excel-connection-manager-editor.md)」を参照してください。  
  
 プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。  
  
 Excel ファイルのグループによるループ処理については、「 [Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する](../control-flow/foreach-loop-container.md)」をご覧ください。  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する](../control-flow/foreach-loop-container.md)  
  
-   [SQL Server Integration Services (SSIS) を使用して、Excel からデータをインポートする、または Excel にデータをエクスポートする](../load-data-to-from-excel-with-ssis.md)
  
  
