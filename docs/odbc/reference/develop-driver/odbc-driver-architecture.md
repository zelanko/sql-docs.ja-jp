---
title: "ODBC ドライバーのアーキテクチャ |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC drivers [ODBC], architecture
ms.assetid: 21a62c7c-192e-4718-a16e-aa12b0de4419
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 39477161fd3eac02912fd371a873b94ea9f51828
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-driver-architecture"></a>ODBC ドライバーのアーキテクチャ
ドライバーの作成者は、ドライバーのアーキテクチャはことができます、アプリケーションは、DBMS に固有の SQL を使用しているかどうかに影響を及ぼすにする必要があります。  
  
 ![ODBC ドライバーのアーキテクチャを示しています](../../../odbc/reference/develop-driver/media/odbcdriverovruarch.gif "ODBCDriverOvruArch。")  
  
 [ファイル ベースのドライバー](../../../odbc/reference/file-based-drivers.md)  
  
 ドライバーは、物理的なデータを直接アクセスする場合、ドライバーはドライバーとデータの両方のソースとして機能します。 ドライバーは、ODBC 呼び出しと SQL ステートメントの両方を処理する必要があります。 ファイル ベースのドライバーの開発者は、独自のデータベース エンジンを記述する必要があります。  
  
 [DBMS に基づいたドライバー](../../../odbc/reference/dbms-based-drivers.md)  
  
 別のデータベース エンジンを使用して、物理データにアクセスする、ドライバーは ODBC の呼び出しのみを処理します。 SQL ステートメントに渡すには、データベース エンジンを処理します。  
  
 [ネットワーク アーキテクチャ](../../../odbc/reference/network-example.md)  
  
 ファイルと DBMS ODBC の構成は、1 つのネットワークに存在できます。  
  
 [他のドライバーのアーキテクチャ](../../../odbc/reference/other-driver-architectures.md)  
  
 をさまざまなデータ ソースを使用するドライバーが必要な場合は、ミドルウェアとして使用できます。 異種結合エンジンのアーキテクチャでは、ドライバー マネージャーとして表示される、ドライバーをことができます。 ドライバーは、一連のクライアントで共有できる、サーバーにもインストールできます。  
  
 ドライバーのアーキテクチャの詳細については、次を参照してください。[ドライバー マネージャー](../../../odbc/reference/the-driver-manager.md)と[ドライバーのアーキテクチャ](../../../odbc/reference/driver-architecture.md) セクションで[ODBC アーキテクチャ](../../../odbc/reference/odbc-architecture.md)です。  
  
 ドライバーの問題の詳細については、次の表で説明した場所にあります。  
  
|問題点|トピック|場所|  
|-----------|-----------|--------------|  
|アプリケーションおよびドライバーとの互換性の問題|[アプリケーション/ドライバーの互換性](../../../odbc/reference/develop-app/application-and-driver-compatibility.md)|[プログラミングに関する考慮事項](../../../odbc/reference/develop-app/programming-considerations.md)、ODBC プログラマ リファレンス|  
|ODBC ドライバーの記述|[書き込み ODBC 3.x ドライバー](../../../odbc/reference/develop-app/writing-odbc-3-x-drivers.md)|[プログラミングに関する考慮事項](../../../odbc/reference/develop-app/programming-considerations.md)、ODBC プログラマ リファレンス|  
|旧バージョンとの互換性のためのドライバーのガイドライン|[旧バージョンとの互換性のためのドライバーのガイドライン](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md)|[付録 g: 旧バージョンとの互換性のためドライバー ガイドライン](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md)、ODBC プログラマ リファレンス|  
|ドライバーへの接続|[データを選択するソースまたはドライバー](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)|[データに接続するソースまたはドライバー](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md)、ODBC プログラマ リファレンス|  
|ドライバーを識別します。|[ドライバーの表示](../../../odbc/admin/viewing-drivers.md)|[ドライバーを表示する](../../../odbc/admin/viewing-drivers.md)、Microsoft ODBC データ ソース アドミニストレーターのオンライン ヘルプ|  
|接続プールを有効にします。|[ODBC 接続プール](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)|[データに接続するソースまたはドライバー](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md)、ODBC プログラマ リファレンス|  
|UNICODE/ANSI ドライバーとの接続の問題|[Unicode のドライバー](../../../odbc/reference/develop-app/unicode-drivers.md)|[プログラミングに関する考慮事項](../../../odbc/reference/develop-app/programming-considerations.md)、ODBC プログラマ リファレンス|  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)

