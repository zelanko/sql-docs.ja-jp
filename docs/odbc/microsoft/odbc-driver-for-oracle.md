---
title: オラクル用の ODBC ドライバ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC]
- ODBC driver for Oracle [ODBC], about ODBC driver for Oracle
- Oracle data access [ODBC]
ms.assetid: 937e0662-8b1d-44f7-b077-4015c6605b2c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 093cb7352a7f509b0afcc061e2691311bb183169
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298132"
---
# <a name="odbc-driver-for-oracle"></a>ODBC Driver for Oracle
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle 用のマイクロソフト® ODBC ドライバーを使用すると、ODBC 準拠のアプリケーションを Oracle データベースに接続できます。 Oracle 用 ODBC ドライバは、ODBC プログラマ リファレンス で説明されているオープン データベース接続 *(ODBC)* 仕様に準拠しています。 PL/SQLパッケージ、XA/DTC統合、およびインターネットインフォメーションサービス(IIS)内からのオラクルアクセスへのアクセスを可能にします。  
  
 Oracle RDBMS は、さまざまなワークステーションおよびミニコンピュータ オペレーティング システムで実行されるマルチユーザー リレーショナル データベース管理システムです。 マイクロソフトの Windows を実行している IBM 互換のコンピュータは、ネットワーク経由で Oracle データベース サーバーと通信できます。 サポートされるネットワークには、マイクロソフト LAN マネージャ、ネットウェア、VINES、DECnet、および TCP/IP をサポートする任意のネットワークが含まれます。  
  
 Oracle 用 ODBC ドライバーを使用すると、アプリケーションは ODBC インターフェイスを使用して Oracle データベース内のデータにアクセスできます。 ドライバは、ローカルの Oracle データベースにアクセスすることも、SQL*Net を介してネットワークと通信することもできます。 次の図は、このアプリケーションとドライバーのアーキテクチャの詳細を示しています。  
  
 ![Oracle アプリ&#47;ドライバー アーキテクチャ用の ODBC ドライバ](../../odbc/microsoft/media/orcdrvsdkarch.gif "オルクドヴSDKアーチ")  
  
 Oracle 用 ODBC ドライバは、API 準拠レベル 1 および SQL 準拠レベル コアに準拠しています。 また、API 準拠レベル 2 の関数と、コアおよび拡張 SQL 準拠レベルの文法の大部分もサポートしています。 ドライバーは ODBC 2.5 準拠で、32 ビット システムをサポートしています。 Oracle 7.3xは完全にサポートされています。Oracle8 のサポートは限られています。 Oracle 用 ODBC ドライバーは、新しい Oracle8 データ型 (Unicode データ型、BLOB、CLOB など) をサポートせず、また Oracle の新しいリレーショナル オブジェクト モデルもサポートしていません。 サポートされるデータ型の詳細については、このガイドの[「サポートされるデータ型](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md)」を参照してください。  
  
 Oracleデータにアクセスするには、次のコンポーネントが必要です。  
  
-   オラクル用の ODBC ドライバ  
  
-   オラクル RDBMS データベース  
  
-   オラクル・クライアント・ソフトウェア  
  
 さらに、リモート接続の場合:  
  
-   ドライバとデータベースを実行するコンピュータを接続するネットワーク。 ネットワークは SQL*Net 接続をサポートしている必要があります。  
  
## <a name="component-documentation"></a>コンポーネントのドキュメント  
 このガイドには、Oracle 用 Microsoft ODBC ドライバーのセットアップと構成、およびプログラムによる機能の追加に関する詳細情報が記載されています。 また、技術参考資料も含まれています。  
  
 特定のOracle製品の動作については、Oracle製品に付属のマニュアルを参照してください。  
  
 ODBC データ ソース アドミニストレータを使用して Oracle 用 Microsoft ODBC ドライバを設定または構成する方法については[、ODBC データ ソース アドミニストレータ](../../odbc/admin/odbc-data-source-administrator.md)のマニュアルを参照してください。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ODBC Driver for Oracle ユーザー ガイド](../../odbc/microsoft/odbc-driver-for-oracle-user-s-guide.md)  
  
-   [ODBC Driver for Oracle プログラマー向けリファレンス](../../odbc/microsoft/odbc-driver-for-oracle-programmer-s-reference.md)
