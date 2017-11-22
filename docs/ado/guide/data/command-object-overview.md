---
title: "コマンド オブジェクトの概要 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: command object [ADO]
ms.assetid: e84a14b1-3c2a-4f7d-a966-9e08a93948df
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8f1f01c7ca7a378faaaabf11099b97b0dfa0c7a2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="command-object-overview"></a>コマンド オブジェクトの概要
**コマンド**オブジェクトを次を行うことができます。  
  
-   使用して、実行可能コマンドのテキスト、(たとえば、SQL ステートメントまたはストアド プロシージャ) を定義、 **CommandText**プロパティです。  
  
-   使用してパラメーター化クエリまたはストアド プロシージャの引数を定義する**パラメーター**オブジェクトおよび**パラメーター**コレクション。  
  
-   コマンドを実行し、返す、 **Recordset**オブジェクト、必要に応じてを使用して、 **Execute**メソッドです。  
  
-   使用して、コマンドの種類を指定、 **CommandType**パフォーマンスを最適化するために実行する前にプロパティです。  
  
-   使用して、コマンド テキストに関する特定の情報を指定、 **Dialect**のプロパティ、**コマンド**オブジェクト。  
  
-   プロバイダーを使用して実行する前に、コマンドの準備 (またはコンパイル済み) のバージョンを保存するかどうかを制御、 **Prepared**プロパティです。  
  
-   プロバイダーがコマンドを使用して実行を待機する秒数を設定、 **CommandTimeout**プロパティです。  
  
-   開いている接続に関連付ける、**コマンド**オブジェクトを設定してその**ActiveConnection**プロパティです。  
  
-   設定、**名前**プロパティを識別する、**コマンド**オブジェクト、関連するメソッドとして**接続**オブジェクト。  
  
-   渡す、**コマンド**オブジェクトを**ソース**のプロパティ、 **Recordset**データを取得するためにします。  
  
-   渡す、**ストリーム**コマンド (たとえば、XML コマンド) がサポートされているプロバイダーに格納しているオブジェクト。
