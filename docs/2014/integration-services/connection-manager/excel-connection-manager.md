---
title: Excel 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- files [Integration Services], connections
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: 667419f2-74fb-4b50-b963-9197d1368cda
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 5c853ba0255f0e1afc511465de6c31a62376bf4c
ms.sourcegitcommit: d463f543e8db4a768f8e9736ff28fedb3fb17b9f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2018
ms.locfileid: "36324696"
---
# <a name="excel-connection-manager"></a>Excel 接続マネージャー
  Excel 接続マネージャーを使用すると、パッケージは既存の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel ブック ファイルに接続できます。 Excel ソースおよび Excel 変換先を[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]含める Excel 接続マネージャーを使用します。  
  
 Excel 接続マネージャーをパッケージに追加するときに、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] により、実行時に Excel 接続として解決される接続マネージャーを作成し、接続マネージャーのプロパティを設定して、接続マネージャーをパッケージの `Connections` コレクションに追加します。  
  
 `ConnectionManagerType`接続マネージャーのプロパティに設定されて`EXCEL`です。  
  
> [!NOTE]  
>  パスワードで保護された Excel ファイルには接続できません。  
  
## <a name="configuration-of-the-excel-connection-manager"></a>Excel 接続マネージャーの構成  
 Excel 接続マネージャーは、次の方法で構成できます。  
  
-   Excel ブック ファイルのパスを指定します。  
  
-   ファイルの作成に使用した Excel のバージョンを指定します。  
  
-   選択したワークシート内または範囲内でアクセスするデータの最初の行に、列名が格納されているかどうかを示します。  
  
 Excel ソースによって Excel 接続マネージャーが使用された場合は、抽出したデータに列名が含められます。 Excel 変換先によって使用された場合は、出力されたデータに列名が含められます。  
  
 Excel 接続マネージャーを使用して、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 とサポートの Excel ISAM (Indexed Sequential Access Method) ドライバーの接続、読み取りし、Excel データ ソースにデータを書き込むにします。 このプロバイダーとドライバーの Excel ソースおよび Excel 変換先で使用する場合の動作に関する詳細については、次を参照してください。 [Excel ソース](../data-flow/excel-source.md)と[Excel 変換先](../data-flow/excel-destination.md)です。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [Excel 接続マネージャー](../excel-connection-manager-editor.md)」を参照してください。  
  
 プログラムによる接続マネージャーの構成方法の詳細については、次を参照してください。<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>と[プログラムで接続を追加する](../building-packages-programmatically/adding-connections-programmatically.md)です。  
  
 Excel ファイルのグループによるループ処理については、「 [Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する](../control-flow/foreach-loop-container.md)」をご覧ください。  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する](../control-flow/foreach-loop-container.md)  
  
-   [SQL Server Integration Services (SSIS) を使用して、Excel からデータをインポートする、または Excel にデータをエクスポートする](../load-data-to-from-excel-with-ssis.md)
  
  