---
title: コマンド オブジェクトの概要 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- command object [ADO]
ms.assetid: e84a14b1-3c2a-4f7d-a966-9e08a93948df
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cdb2d323b57a63d0ffc84044ece0604571d04164
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
