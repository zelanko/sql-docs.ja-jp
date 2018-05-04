---
title: ODBC Driver for Oracle |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC]
- ODBC driver for Oracle [ODBC], about ODBC driver for Oracle
- Oracle data access [ODBC]
ms.assetid: 937e0662-8b1d-44f7-b077-4015c6605b2c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a129bbc39f35c2418fc0dc5d34e534d4c7fb8cbc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-driver-for-oracle"></a>ODBC Driver for Oracle
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Microsoft® ODBC Driver for Oracle では、Oracle データベースを ODBC 準拠のアプリケーションに接続することができます。 ODBC Driver for Oracle で説明されているオープン データベース コネクティビティ (ODBC) の仕様に準拠、 *ODBC プログラマ リファレンス*です。 PL/SQL パッケージ、XA/DTC 統合、および Oracle からのアクセスにインターネット インフォメーション サービス (IIS) へアクセスを許可します。  
  
 Oracle RDBMS は、ワークステーションとミニのさまざまなオペレーティング システムで実行されるマルチ ユーザーのリレーショナル データベース管理システムです。 Microsoft Windows を実行している IBM 互換コンピューターは、ネットワーク経由で Oracle データベース サーバーと通信できます。 サポートされているネットワークには、Microsoft LAN Manager、NetWare、VINES、DECnet、および TCP/IP をサポートするネットワークが含まれます。  
  
 Oracle 用の ODBC ドライバーにより、アプリケーションを ODBC インターフェイスを通じて Oracle データベースでデータにアクセスします。 ドライバーがローカルの Oracle データベースにアクセスできるか、SQL を使用するネットワークと通信できる * Net です。 次の図では、このアプリケーションとドライバーのアーキテクチャについて説明します。  
  
 ![Oracle アプリケーション用の ODBC ドライバー&#47;ドライバーのアーキテクチャ](../../odbc/microsoft/media/orcdrvsdkarch.gif "OrcDrvSDKArch")  
  
 ODBC Driver for Oracle は、API への準拠レベル 1 および SQL への準拠レベル コアに準拠します。 API への準拠レベル 2 とほとんどのコアと拡張 SQL への準拠レベル文法の一部の関数もサポートしています。 ドライバーは ODBC 2.5 に準拠し、32 ビット システムをサポートしています。 Oracle 7.3 x はサポートされている完全;Oracle8 には、サポートが制限されています。 For Oracle ODBC ドライバーには新しい Oracle8 データ型はサポートされません: Unicode データ型、Blob、Clob、具合 — もサポート Oracle の新規のリレーショナル オブジェクト モデルです。 サポートされるデータ型の詳細については、次を参照してください。 [Supported Data Types](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md)このガイドでします。  
  
 Oracle データにアクセスするには、次のコンポーネントが必要です。  
  
-   ODBC Driver for Oracle  
  
-   RDBMS の Oracle データベース  
  
-   Oracle クライアント ソフトウェア  
  
 さらのリモート接続は。  
  
-   ドライバーと、データベースを実行しているコンピューターを接続するネットワーク。 ネットワークは、SQL をサポートする必要があります * Net 接続します。  
  
## <a name="component-documentation"></a>コンポーネントのドキュメント  
 このガイドを設定して、Microsoft ODBC Driver for Oracle を構成してプログラムの機能の追加に関する詳細情報が含まれています。 技術参考資料も含まれています。  
  
 特定の Oracle 製品の動作に関する情報は、Oracle 製品に付属するマニュアルを参照してください。  
  
 設定するか、Microsoft ODBC Driver for Oracle、ODBC データ ソース アドミニストレーターを使用して構成する方法については、次を参照してください。、 [ODBC データ ソース アドミニストレーター](../../odbc/admin/odbc-data-source-administrator.md)ドキュメント。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ODBC Driver for Oracle ユーザー ガイド](../../odbc/microsoft/odbc-driver-for-oracle-user-s-guide.md)  
  
-   [ODBC Driver for Oracle プログラマー向けリファレンス](../../odbc/microsoft/odbc-driver-for-oracle-programmer-s-reference.md)
