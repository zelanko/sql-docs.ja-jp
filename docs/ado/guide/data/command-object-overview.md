---
title: Command オブジェクトの概要 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- command object [ADO]
ms.assetid: e84a14b1-3c2a-4f7d-a966-9e08a93948df
author: rothja
ms.author: jroth
ms.openlocfilehash: 0048765d3a5f5cb57419f9dbd755790c9931e218
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761198"
---
# <a name="command-object-overview"></a>Command オブジェクトの概要
**Command**オブジェクトを使用すると、次の操作を実行できます。  
  
-   **CommandText**プロパティを使用して、コマンドの実行可能テキスト (SQL ステートメントやストアドプロシージャなど) を定義します。  
  
-   **パラメーター**オブジェクトと**Parameters**コレクションを使用して、パラメーター化クエリまたはストアドプロシージャの引数を定義します。  
  
-   **Execute**メソッドを使用して、コマンドを実行し、必要に応じて**レコードセット**オブジェクトを返します。  
  
-   実行前に**CommandType**プロパティを使用してコマンドの種類を指定し、パフォーマンスを最適化します。  
  
-   **Command オブジェクトの** **Dialect**プロパティを使用して、コマンドテキストに関する特定の情報を指定します。  
  
-   **準備されたプロパティを**使用して、準備済み (またはコンパイル済み) のコマンドを実行前にプロバイダーが保存するかどうかを制御します。  
  
-   **CommandTimeout**プロパティを使用して、プロバイダーがコマンドの実行を待機する秒数を設定します。  
  
-   **ActiveConnection**プロパティを設定して、開いている接続を**Command**オブジェクトに関連付けます。  
  
-   **Name**プロパティを設定して、関連付けられている**接続**オブジェクトのメソッドとして**コマンド**オブジェクトを識別します。  
  
-   データを取得するために、**レコードセット**の**Source**プロパティに**Command**オブジェクトを渡します。  
  
-   コマンドを含む**ストリーム**オブジェクト (XML コマンドなど) を、それをサポートするプロバイダーに渡します。
