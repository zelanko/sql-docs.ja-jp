---
title: Microsoft Connector for Oracle | Microsoft Docs
ms.custom: ''
ms.date: 08/14/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ee00232a1c1e64d31b7b6360666bdeebba756db9
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75246950"
---
# <a name="microsoft-connector-for-oracle"></a>Microsoft Connector for Oracle

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

Microsoft Connector for Oracle を使用すると、SSIS パッケージ内の Oracle データソースで、データのエクスポートとデータの読み込みを実行できます。

## <a name="version-support"></a>バージョンのサポート

Microsoft Connector for Oracle では、次の Microsoft SQL Server 製品がサポートされています。

- SQL Server 2019 以降
- SQL Server Data Tools (SSDT)

次の Oracle データベース バージョンのデータ ソースがサポートされています。

- Oracle 10.x
- Oracle 11.x
- Oracle 12c
- Oracle 18c (Windows 認証のサポートなし)

Oracle データベースは、すべてのオペレーティング システムとプラットフォームでサポートされています。
> [!NOTE]
>
> SQL Server 2019 では、Microsoft Connector for Oracle Database 用の Oracle クライアントは必要ありません。

## <a name="installation"></a>インストール

SQL Server でパッケージを実行する必要がある場合は、[こちら](https://www.microsoft.com/download/details.aspx?id=58228)から Microsoft Connector for Oracle Database インストール プログラムを取得できます。 そのうえでインストール ウィザードの指示に従います。

コネクタをインストールしたら、SQL Server 統合サービスを再起動して、Oracle のソースと変換先が正常に機能することを確認する必要があります。

コネクタを含むパッケージを設計する必要がある場合は、コネクタをダウンロードする必要はありません。 バージョン 15.9.0 以降の SQL Server Data Tools (SSDT) には、それが含まれています。

## <a name="uninstallation"></a>アンインストール

アンインストール ウィザードを実行して、SQL Server から Microsoft Connector for Oracle Database を削除できます。

## <a name="design-ssis-package-with-previous-version"></a>以前のバージョンで SSIS パッケージを設計する

バージョン 15.9.0 以降の SSDT には、Microsoft Connector for Oracle Database が既に含まれているため、SQL Server 2019 をターゲットとする SSIS パッケージを設計する場合、インストールは必要ありません。

SQL Server 2017 以前をターゲットとする SSIS パッケージを設計するには、対応するバージョンの Connector for Oracle by Attunity をインストールする必要があります。

**ダウンロード リンク:**

- [SQL Server 2017:Microsoft Connector Version 5.0 for Oracle by Attunity](https://www.microsoft.com/download/details.aspx?id=55179)
- [SQL Server 2016:Microsoft Connector Version 4.0 for Oracle by Attunity](https://www.microsoft.com/download/details.aspx?id=52950)
- [SQL Server 2014:Microsoft Connector Version 3.0 for Oracle by Attunity](https://www.microsoft.com/download/details.aspx?id=44582)
- [SQL Server 2012:Microsoft Connector Version 2.0 for Oracle by Attunity](https://www.microsoft.com/download/details.aspx?id=29283)

## <a name="next-steps"></a>次のステップ

- [Oracle 接続マネージャー](oracle-connection-manager.md)を構成する。
- [Oracle ソース](oracle-source.md)を構成する。
- [Oracle 変換先](oracle-destination.md)を構成する。
- ご質問がある場合は、[技術者コミュニティ](https://aka.ms/AA5u35j)を参照してください。
