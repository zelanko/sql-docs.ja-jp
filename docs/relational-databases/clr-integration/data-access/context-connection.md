---
title: コンテキスト接続 |マイクロソフトドキュメント
description: Microsoft SQL Server では、コンテキスト接続を使用すると、コードが呼び出されたのと同じコンテキストで Transact-SQL ステートメントを実行できます。
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context connections [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- context [CLR integration]
ms.assetid: 67dd1925-d672-4986-a85f-bce4fe832ef7
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f29914557e3a1c1e7a929bec22a2b55d0db2a50
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81485522"
---
# <a name="context-connection"></a>コンテキスト接続
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  内部データへのアクセスに関する問題は、ごく一般的なものです。 内部データにアクセスすることは、CLR (共通言語ランタイム) ストアド プロシージャや関数を実行しているサーバーへのアクセスを考えることです。 1 つのオプションは **、System.Data.SqlClient.SqlConnection**を使用して接続を作成し、ローカル サーバーを指す接続文字列を指定し、接続を開く方法です。 これには、ログインのための資格情報を指定することが必要になります。 接続は、ストアド プロシージャや関数とは異なるデータベース セッション内にあり **、SET**オプションが異なる場合、別のトランザクション内にある場合、一時テーブルを参照できないなどです。 マネージド ストアド プロシージャや関数のコードが SQL Server プロセスで実行されているということは、だれかがそのサーバーに接続して、マネージド コードを呼び出す SQL ステートメントを実行したことを意味します。 ストアド プロシージャまたは関数は、トランザクションや**SET**オプションなどと共に、その接続のコンテキストで実行する必要があります。 これを "コンテキスト接続" と呼びます。  
  
 コンテキスト接続を使用すると、コードを最初に呼び出したのと同じコンテキストで Transact-SQL ステートメントを実行することができます。 コンテキスト接続を取得するには、次の例に示すように "context connection" 接続文字列キーワードを使用する必要があります。  
  
 [C#]  
  
```  
using(SqlConnection connection = new SqlConnection("context connection=true"))   
{  
    connection.Open();  
    // Use the connection  
}  
```  
  
 [Visual Basic]  
  
```  
Using connection as new SqlConnection("context connection=true")  
    connection.Open()  
    ' Use the connection  
End Using  
  
```  
  
## <a name="in-this-section"></a>このセクションの内容  
 [通常の接続とコンテキスト接続](../../../relational-databases/clr-integration/data-access/context-connections-vs-regular-connections.md)  
 通常の接続とコンテキスト接続の違いについて説明します。  
  
 [通常の接続とコンテキスト接続に関する制限事項](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md)  
 通常の接続とコンテキスト接続の制限事項について説明します。  
  
  
