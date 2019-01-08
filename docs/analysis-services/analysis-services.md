---
title: SQL Server Analysis Services の概要 |Microsoft Docs
ms.date: 12/05/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: overview
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b2cd892ad41beba2b5715b3a7186ae5e44bb7911
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591778"
---
# <a name="about-sql-server-analysis-services"></a>SQL Server Analysis Services の概要

Analysis Services は、意思決定支援とビジネス分析で使用される分析データ エンジンです。 提供エンタープライズ グレード セマンティック データ モデルのビジネス レポートおよび Power BI、Excel、Reporting Services レポート、およびその他のデータ視覚化ツールなどのクライアント アプリケーション。

一般的なワークフローには、Visual Studio でデータを表形式または多次元モデル プロジェクトの作成、サーバー インスタンスにデータベースとしてモデルを展開する、定期的なデータ処理、設定、およびエンドユーザーによってデータ アクセスを許可するアクセス許可の割り当てが含まれています。 準備ができましたが、セマンティック データ モデルをデータ ソースとして Analysis Services をサポートしているクライアント アプリケーションによってアクセスできます。

Analysis Services は、2 つの異なるプラットフォームで使用できます。

**Azure Analysis Services** -1200 以降の互換性レベル表形式モデルをサポートしています。 DirectQuery、パーティション、行レベルのセキュリティ、双方向のリレーションシップ、および翻訳がすべてサポートされます。 詳細についてを参照してください。 [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/)します。

**SQL Server Analysis Services** -SharePoint のすべての互換性レベルは、多次元モデル、データ マイニング、および Power Pivot の表形式モデルをサポートしています。

## <a name="documentation-by-area"></a>領域別のドキュメント

般的に、 [Azure Analysis Services に関するドキュメントは](https://docs.microsoft.com/azure/analysis-services/) Azure のドキュメントに含まれます。 クラウドに、表形式モデルに知りたい場合は、最初にことをお勧めします。 この記事とこのセクションでは、SQL Server Analysis Services のほとんどの場合は。 しかし、少なくとも表形式モデルに関しては、どのプラットフォームを使用しているかに関わらず、プロジェクトの作成方法と展開方法は同じです。 詳細については、これらのセクションをご覧ください。

- [テーブル ソリューションと多次元ソリューションの比較](../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)
- [SQL Server Analysis Services をインストールします。](../analysis-services/instances/install-windows/install-analysis-services.md)
- [テーブル モデル](../analysis-services/tabular-models/tabular-models-ssas.md)
- [多次元モデル](../analysis-services/multidimensional-models/multidimensional-models-ssas.md)
- [データ マイニング](../analysis-services/data-mining/data-mining-ssas.md)
- [Power Pivot for SharePoint](../analysis-services/power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)
- [チュートリアル](../analysis-services/analysis-services-tutorials-ssas.md)
- [サーバーの管理](../analysis-services/instances/analysis-services-instance-management.md)
- [開発者向けドキュメント](analysis-services-developer-documentation.md)
- [テクニカル リファレンス](https://docs.microsoft.com/bi-reference/)

#### <a name="see-also"></a>関連項目

[Azure Analysis Services のドキュメント](https://docs.microsoft.com/azure/analysis-services/)
[SQL Server のドキュメント](../sql-server/sql-server-technical-documentation.md)
