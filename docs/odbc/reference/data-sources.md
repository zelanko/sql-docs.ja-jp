---
title: "データ ソース | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data sources [ODBC]
- data sources [ODBC], about data sources
ms.assetid: 4ae44fa2-0b9b-4e19-ab45-c1dc93b68406
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.openlocfilehash: 84c415fd10a757cebfc365759d7fb038f9630ec4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="data-sources"></a>ソリューション エクスプローラー
A*データソース*データのソースだけです。 ファイル、DBMS、またはライブ データ フィードではさらに特定のデータベースがあります。 データをプログラムと同じコンピューター上またはネットワーク上のどこか別のコンピューター上にあることがあります。 たとえば、データ ソースは、Novell® Netware; によってアクセス OS/2® オペレーティング システムで実行されている Oracle DBMS 可能性があります。ゲートウェイ経由でアクセス IBM DB2 DBMSXbase ディレクトリにあるファイル サーバー以外のコレクションまたは、ローカルの Microsoft® Access データベース ファイルを選択します。  
  
 データ ソースの目的は、すべてのデータにアクセスするために必要な技術的な情報を収集する — ドライバー名、ネットワーク アドレス、ネットワーク ソフトウェア、およびよびな —、1 つに配置し、ユーザーに対して非表示にします。 ユーザーを給与、インベントリ、および担当者の一覧を見て、リストから、給与を選択し、アプリケーションの給与データが存在するかして、アプリケーションの経緯を知らなくてもすべて、給与データに接続できる必要があります。  
  
 用語*データソース*のような用語と混同しないでです。 このマニュアルで*DBMS*または*データベース*データベース プログラムまたはエンジンを表します。 さらに区別されている*デスクトップ データベースは、*パーソナル コンピューターで実行するに設計され、多くの場合、フル SQL とトランザクションのサポート、不足していると*server データベース、*クライアントで実行するよう設計されています/サーバー環境ではスタンドアロン データベース エンジンと豊富な SQL とトランザクションのサポートを特徴とします。 *データベース*Xbase 上のファイルのディレクトリまたはデータベース内の SQL Server のコレクションなどのデータの特定のコレクションを指すこともできます。 用語に通常と同じである*カタログ、*このマニュアルまたは用語で別の場所で使用*修飾子*ODBC の以前のバージョン。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [データ ソースの種類](../../odbc/reference/types-of-data-sources.md)  
  
-   [データ ソースの使用](../../odbc/reference/using-data-sources.md)  
  
-   [データ ソースの例](../../odbc/reference/data-source-example.md)
