---
title: ODBC ドライバのアーキテクチャ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], architecture
ms.assetid: 21a62c7c-192e-4718-a16e-aa12b0de4419
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 712de6a7a3f80ce1cd3ca854a88765dbfa531356
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294560"
---
# <a name="odbc-driver-architecture"></a>ODBC ドライバーのアーキテクチャ
ドライバーの作成者は、ドライバーアーキテクチャがアプリケーションが DBMS 固有の SQL を使用できるかどうかに影響を与える可能性があることに注意する必要があります。  
  
 ![ODBC ドライバーのアーキテクチャ](../../../odbc/reference/develop-driver/media/odbcdriverovruarch.gif "ODBCドライバーヴォヴルアーチ")  
  
 [ファイルベースのドライバ](../../../odbc/reference/file-based-drivers.md)  
  
 ドライバーは、物理データに直接アクセスするとき、ドライバーは、ドライバーとデータ ソースの両方として機能します。 ドライバーは、ODBC 呼び出しと SQL ステートメントの両方を処理する必要があります。 ファイル ベースのドライバーの開発者は、独自のデータベース エンジンを記述する必要があります。  
  
 [DBMS ベースのドライバー](../../../odbc/reference/dbms-based-drivers.md)  
  
 物理データへのアクセスに別のデータベース エンジンを使用する場合、ドライバーは ODBC 呼び出しのみを処理します。 SQL ステートメントをデータベース エンジンに渡して処理します。  
  
 [ネットワーク アーキテクチャ](../../../odbc/reference/network-example.md)  
  
 ファイルおよび DBMS ODBC の構成は、単一のネットワーク上に存在できます。  
  
 [その他のドライバーのアーキテクチャ](../../../odbc/reference/other-driver-architectures.md)  
  
 ドライバがさまざまなデータ ソースを操作する必要がある場合は、ミドルウェアとして使用できます。 異種結合エンジンアーキテクチャは、ドライバーマネージャーとしてドライバーを表示できます。 ドライバーは、一連のクライアントで共有できるサーバーにインストールすることもできます。  
  
 ドライバー アーキテクチャの詳細については、ODBC アーキテクチャのセクションで[ドライバー マネージャー](../../../odbc/reference/the-driver-manager.md)と[ドライバー](../../../odbc/reference/driver-architecture.md)[のアーキテクチャを参照](../../../odbc/reference/odbc-architecture.md)してください。  
  
 ドライバーの問題の詳細については、次の表で説明する場所を参照してください。  
  
|問題|トピック|場所|  
|-----------|-----------|--------------|  
|アプリケーションとドライバーの互換性の問題|[アプリケーション/ドライバの互換性](../../../odbc/reference/develop-app/application-and-driver-compatibility.md)|[プログラミングに関する考慮事項](../../../odbc/reference/develop-app/programming-considerations.md): ODBC プログラマ リファレンス|  
|ODBC ドライバの作成|[ODBC 3.x ドライバーの作成](../../../odbc/reference/develop-app/writing-odbc-3-x-drivers.md)|[プログラミングに関する考慮事項](../../../odbc/reference/develop-app/programming-considerations.md): ODBC プログラマ リファレンス|  
|下位互換性のためのドライバガイドライン|[ドライバーの下位互換性のガイドライン](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md)|付録 G: ODBC プログラマ リファレンス の[後方互換性に関するドライバのガイドライン](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md)|  
|ドライバーへの接続|[データ ソースまたはドライバーの選択](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)|ODBC プログラマ リファレンス[のデータ ソースまたはドライバへの接続](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md)|  
|ドライバーの識別|[ドライバーの表示](../../../odbc/admin/viewing-drivers.md)|[ODBC](../../../odbc/admin/viewing-drivers.md)データ ソース アドミニストレータ のオンライン ヘルプでドライバを表示する|  
|接続プールの有効化|[ODBC 接続プール](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)|ODBC プログラマ リファレンス[のデータ ソースまたはドライバへの接続](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md)|  
|ユニコード/ANSIドライバと接続の問題|[Unicode ドライバー](../../../odbc/reference/develop-app/unicode-drivers.md)|[プログラミングに関する考慮事項](../../../odbc/reference/develop-app/programming-considerations.md): ODBC プログラマ リファレンス|  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
