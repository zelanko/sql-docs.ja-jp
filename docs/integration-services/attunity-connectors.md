---
title: "Microsoft Connectors for Oracle and Teradata by Attunity (SSIS) |Microsoft ドキュメント"
ms.date: 05/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 926c0c51b5a55a2869b73666f5620fa56e139cca
ms.openlocfilehash: fd8b0177227167f6caa3417029bb2acb974fe181
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="microsoft-connectors-for-oracle-and-teradata-by-attunity-for-integration-services-ssis"></a>Microsoft Connectors for Oracle and Teradata by Attunity for Integration Services (SSIS)

SSIS パッケージ内に、または Oracle または Teradata からのデータの読み込み時のパフォーマンスを最適化する by Attunity の Integration Services のコネクタをダウンロードできます。

## <a name="download-the-latest-attunity-connectors"></a>最新の Attunity コネクタをダウンロードします。

ここでのコネクタの最新バージョンを取得するには。  
[Oracle および Teradata 用の Microsoft Connectors v5.0](https://www.microsoft.com/download/details.aspx?id=55179)

## <a name="issue---the-attunity-connectors-arent-visible-in-the-ssis-toolbox"></a>問題 - Attunity コネクタは、SSIS ツールボックスに表示されません。

SSIS ツールボックス Attunity コネクタを表示するには、常にインストールする必要がターゲットの SQL Server Data Tools (SSDT) のバージョンと同じバージョンの SQL Server インストールされていること、コンピューターにコネクタのバージョン。 (するがありますも以前のバージョンのコネクタをインストールします。)この要件は、SSIS プロジェクトとパッケージの対象となる SQL Server のバージョンに依存しないです。

たとえば、最新バージョンの SSDT をインストールしている場合がある 17 のバージョンの SSDT ビルド番号が 14 で始まる。 このバージョンの SSDT では、SQL Server 2017 のサポートを追加します。 表示し、Attunity を使用して SSIS でのコネクタ パッケージを development - SQL Server の以前のバージョンを対象となる - もバージョン 5.0 Attunity コネクタの最新バージョンをインストールする必要がある場合でもです。 コネクタのこのバージョンでは、SQL Server 2017 のサポートも追加されます。

Visual Studio での SSDT のインストールされているバージョンを確認**ヘルプ** | **に関する Microsoft クトリ**、または**プログラムと機能**コントロール パネルの します。 次の表から Attunity コネクタの対応するバージョンをインストールします。

|SSDT のバージョン|SSDT のビルド番号|ターゲット SQL Server のバージョン|コネクタの必要なバージョン|
|---------|---------|---------|---------|
|17|14 で始まります。|SQL Server 2017|[Oracle および Teradata 用の Microsoft Connectors v5.0](https://www.microsoft.com/download/details.aspx?id=55179)|
|16|13 で始まります。|SQL Server 2016|[Oracle および Teradata 用の Microsoft Connectors v4.0](https://www.microsoft.com/download/details.aspx?id=52950)|
||||

## <a name="download-the-latest-sql-server-data-tools-ssdt"></a>最新 SQL Server Data Tools (SSDT) のダウンロードします。

ここで SSDT の最新バージョンを取得します。  
[SQL Server Data Tools (SSDT) のダウンロード](..//ssdt/download-sql-server-data-tools-ssdt.md)
