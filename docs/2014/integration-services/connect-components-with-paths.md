---
title: パスを使用してコンポーネントを連結する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data flow [Integration Services], connections
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 05633e4c-1370-4b05-802b-f36b07dd71c8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8635ced29f28781bba9d67408ce69f61171ab660
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85434499"
---
# <a name="connect-components-with-paths"></a>パスを使用してコンポーネントを連結する
  パッケージ内にデータ フローを構築するには、 **デザイナーにある** [データ フロー] [!INCLUDE[ssIS](../includes/ssis-md.md)] タブのデザイン画面を使用します。 データ フローにデータ フロー コンポーネントが 2 つ含まれる場合、変換元または変換からの出力を変換または変換先への入力に連結することで、これらのコンポーネントを連結できます。 2 つのデータ フロー コンポーネント間のコネクタは、パスと呼ばれます。

 次の図は、1 つの変換元コンポーネント、2 つの変換、1 つの変換先コンポーネント、およびこれらを連結するパスを持つ、簡単なデータ フローを示しています。

 ![データフロー](media/mw-dts-08.gif "Data flow")

 2 つのコンポーネントを連結したら、パスを移動するデータのメタデータおよびパスのプロパティを、 **[データ フロー パス エディター]** で表示できます。 詳細については、「 [Integration Services のパス](data-flow/integration-services-paths.md)」を参照してください。

 また、データ ビューアーをパスに追加することもできます。 データ ビューアーを使用すると、パッケージの実行時にデータ フロー コンポーネント間を移動するデータを表示できます。

### <a name="to-connect-components-in-a-data-flow"></a>データ フロー内でコンポーネントを連結するには

-   [データ フロー内でコンポーネントを連結する](data-flow/connect-components-in-a-data-flow.md)

### <a name="to-set-path-properties"></a>パスのプロパティを設定するには

-   [データ フロー パス エディターを使用してパスのプロパティを設定する](../../2014/integration-services/set-the-properties-of-a-path-by-using-the-data-flow-path-editor.md)

### <a name="to-view-path-metadata"></a>パスのメタデータを表示するには

-   [データ フロー パス エディターでパスのメタデータを表示する](../../2014/integration-services/view-path-metadata-in-the-data-flow-path-editor.md)

### <a name="to-view-path-metadata"></a>パスのメタデータを表示するには

-   [データ フローにデータ ビューアーを追加する](../../2014/integration-services/add-a-data-viewer-to-a-data-flow.md)

## <a name="see-also"></a>関連項目
 [データフロータスク](control-flow/data-flow-task.md)の[データフロー](data-flow/data-flow.md)変換[を使用したデータの変換](data-flow/transformations/transform-data-with-transformations.md)データ[でのエラー処理](data-flow/error-handling-in-data.md)


