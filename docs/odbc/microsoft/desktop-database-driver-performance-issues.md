---
title: "デスクトップ データベース ドライバー パフォーマンスの問題 |Microsoft ドキュメント"
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
- ODBC desktop database drivers [ODBC], performance
- desktop database drivers [ODBC], performance
- Jet-based ODBC drivers [ODBC], performance
ms.assetid: 1a4c4b7e-9744-411f-9b6e-06dfdad92cf7
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 67379ee540aecb691122d91b42776b0c9d990b1d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="desktop-database-driver-performance-issues"></a>デスクトップ データベース ドライバー パフォーマンスの問題
既存の ANSI アプリケーションとの互換性のために、SQL_WCHAR、SQL_WVARCHAR、SQL_WLONGVARCHAR データ型は Microsoft アクセス 4.0 または上位のデータ ソースとして SQL_CHAR、SQL_VARCHAR、SQL_LONGVARCHAR に公開されます。 データ ソースはデータ型のワイド文字を返しませんが、データもする必要があります送信 jet ワイド文字形式で。 変換が行われる SQL_C_CHAR パラメーターまたは結果の列が、ANSI アプリケーションで SQL_CHAR データ型にバインドされている場合を理解しておく必要があります。  
  
 この変換型 LONGVARCHAR のパラメーターを SQL_C_CHAR 型がバインドされている場合にメモリの観点から、特に効率的なことができます。 Jet 4.0 のエンジンは、長いテキスト パラメーター データをストリームにできないため、UNICODE 変換バッファー割り当てる必要があります、SQL_C_CHAR ANSI バッファーのサイズの 2 倍であります。 UNICODE 変換を実行および型 SQL_C_WCHAR としてパラメーターをバインドするアプリケーションは最も効率的なメカニズムです。 実行時のデータとして、パラメーターをマークすると、SQLPutData に複数の呼び出しで、データを提供、longtext データ バッファーが拡張されます。 SQL_DATA_AT_EXEC_LEN(x)、経由での省略可能な長さを指定する、この成長のコストを回避する方法の 1 つの「データの配置」バッファーが場所*x*バイトの予期された長さです。 これに内部 PutData バッファーのサイズが初期化されます*x*バイトです。  
  
> [!NOTE]  
>  使用して効率的に挿入または長い形式のデータの更新を実現できます**SQLBulkOperations()**または**SQLSetPos()**および SQL_DATA_AT_EXEC を長い形式のデータを設定します。 (このケースで EXEC_LEN を無視) します。呼び出してチャンク単位でデータをストリーミングできます**SQLPutData** 、複数回これは効果的にデータ テーブルを追加します。  
  
 バージョン 4.0 を Microsoft ODBC のデスクトップ データベース ドライバーを使用して Jet 3.5 データベースを使用してアプリケーションをアップグレードすると、パフォーマンスが低下し、ワーキング セット サイズの増加が発生します。 これは、ためと、バージョン 3 です。*x*データベースでは、新しいバージョン 4.0 ドライバーを使用して開くときは、Jet 4.0 を読み込みます。 Jet 4.0 データベースを開くし、データベースが 3 が表示されます。*x*バージョン、Jet 3.5 エンジンは、同様の読み込みと等価のインストール可能な ISAM ドライバーを読み込みます。 パフォーマンスとサイズの低下、Jet 3 を削除します。*x* Jet 4.0 形式のデータベースにデータベースを圧縮する必要があります。 これにより、2 つの Jet エンジンの読み込みを排除され、データへのコード パスを最小限に抑えるされます。  
  
 また、Jet 4.0 のエンジンは、Unicode エンジンです。 すべての文字列が保存され、Unicode で処理します。 ときに、ANSI アプリケーションでは、Jet 3 にアクセスします。*x* Jet 4.0 データベース エンジン、データを使用してデータベースは、Unicode、ANSI に ANSI から変換されます。 場合は、データベースを更新して、バージョン 4.0 の形式を文字列が文字列の変換の 1 つのレベルを削除するだけでなく 1 つだけの Jet エンジンを通過して、データへのコード パスを最小限に抑える、Unicode に変換されます。
