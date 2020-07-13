---
title: パッケージ オブジェクトを表示する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, properties
- properties [Integration Services]
- Package Explorer window [Integration Services]
- packages [Integration Services], properties
- explorer view [Integration Services]
- SSIS packages, properties
- viewing package objects
- SQL Server Integration Services packages, properties
ms.assetid: a85c0245-0a68-4eb0-83b1-9b11df80bd10
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ffe46be35db26186f715b18ba6114732d130e02e
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439879"
---
# <a name="view-package-objects"></a>パッケージ オブジェクトを表示する
  [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーでは、 **[パッケージ エクスプローラー]** タブで、パッケージをエクスプローラー表示できます。 この表示には、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] アーキテクチャのコンテナー階層が反映されます。 パッケージ コンテナーはこの階層の最上層にあり、パッケージを展開すると、そのパッケージ内にある接続、実行可能ファイル、イベント ハンドラー、ログ プロバイダー、優先順位制約、および変数が表示されます。

 実行可能ファイルとは、パッケージ内のコンテナーおよびタスクのことで、イベント ハンドラー、優先順位制約、および変数を含めることができます。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では、入れ子構造の階層のコンテナーがサポートされているため、For ループ コンテナー、Foreach ループ コンテナー、およびシーケンス コンテナーは他の実行可能ファイルを含めることができます。

 パッケージにデータ フローが含まれる場合、 **パッケージ エクスプローラー** にはデータ フロー タスクが一覧表示され、データ フロー コンポーネントを一覧表示する **[コンポーネント]** フォルダーが含まれます。

 **[パッケージ エクスプローラー]** タブでは、パッケージ内のオブジェクトを削除したり、 **[プロパティ]** ウィンドウにアクセスしてオブジェクトのプロパティを表示できます。

 次の図は、簡単なパッケージのツリー ビューを示しています。

 ![[パッケージ エクスプローラー] タブのスクリーンショット](media/packageexplorer.gif "[パッケージ エクスプローラー] タブのスクリーンショット")

### <a name="to-view-package-content"></a>パッケージの内容を表示するには

-   [パッケージ エクスプローラーでパッケージ オブジェクトを表示する](../../2014/integration-services/view-package-objects-in-package-explorer.md)

## <a name="see-also"></a>関連項目
 [Integration Services タスク](control-flow/integration-services-tasks.md) [Integration Services コンテナーの](control-flow/integration-services-containers.md)[優先順位制約](control-flow/precedence-constraints.md) [Integration Services &#40;Ssis](integration-services-ssis-variables.md)&#41; INTEGRATION SERVICES &#40;ssis&#41;[イベントハンドラー](integration-services-ssis-event-handlers.md) Integration Services &#40;ssis&#41; の[ログ記録](performance/integration-services-ssis-logging.md)


