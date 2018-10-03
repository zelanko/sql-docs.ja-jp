---
title: データ ソース | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC]
- data sources [ODBC], about data sources
ms.assetid: 4ae44fa2-0b9b-4e19-ab45-c1dc93b68406
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 479cc73538bf94499f2762cca528d2cec72ff3b7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47675361"
---
# <a name="data-sources"></a>ソリューション エクスプローラー
A*データソース*はデータのソースだけです。 ファイル、DBMS、またはデータ フィードではさらに、特定のデータベースになります。 データをプログラムと同じコンピューター上またはネットワーク上のどこか別のコンピューター上にあることがあります。 たとえば、データ ソースは OS/2® オペレーティング システムを Novell® Netware; からアクセスで実行されている Oracle データベース管理システム可能性があります。ゲートウェイを使用してアクセスを IBM DB2 DBMSサーバー ディレクトリ; Xbase ファイルのコレクションまたは、ローカルの Microsoft® Access データベース ファイル。  
  
 データ ソースの目的は、すべてのデータにアクセスするために必要な技術情報を収集する — ドライバー名、ネットワーク アドレス、ネットワーク ソフトウェア、および具合 — 1 つに配置し、ユーザーから非表示にします。 ユーザーは、給与支払い、在庫、および担当者を含む一覧を確認し、一覧から、給与を選択して、アプリケーションの給与データの保存場所やに、アプリケーションの取得を知らなくてもすべて、給与データに接続できる必要があります。  
  
 用語*データソース*のような用語に混同しない必要があります。 このマニュアルの*DBMS*または*データベース*データベース プログラムまたはエンジンを表します。 さらに区別されている*デスクトップ データベースは、* パーソナル コンピューターで実行して多くの場合、完全な SQL とトランザクションのサポート、不足していると*server データベース、* クライアントで実行するように設計/サーバーの状況でのスタンドアロン データベース エンジンと豊富な SQL とトランザクションのサポートを特徴とします。 *データベース*ディレクトリまたはデータベースに SQL Server 上の Xbase ファイルのコレクションなどのデータの特定のコレクションを指すこともできます。 用語とほぼ同等*カタログ、* この手動または用語で他の場所で使用*修飾子*ODBC の以前のバージョン。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [データ ソースの種類](../../odbc/reference/types-of-data-sources.md)  
  
-   [データ ソースの使用](../../odbc/reference/using-data-sources.md)  
  
-   [データ ソースの例](../../odbc/reference/data-source-example.md)
