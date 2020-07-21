---
title: コンテキスト接続 |Microsoft Docs
description: Microsoft SQL Server では、コンテキスト接続を使用して、コードが呼び出されたのと同じコンテキストで Transact-sql ステートメントを実行できます。
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
ms.openlocfilehash: cd0b57e73757348959a0b8b5f144fbc5c4ef0f8c
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892473"
---
# <a name="context-connection"></a>コンテキスト接続
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  内部データへのアクセスに関する問題は、ごく一般的なものです。 内部データにアクセスすることは、CLR (共通言語ランタイム) ストアド プロシージャや関数を実行しているサーバーへのアクセスを考えることです。 1つの方法として、**システム**を使用して接続を作成し、ローカルサーバーを参照する接続文字列を指定して、接続を開く方法があります。 これには、ログインのための資格情報を指定することが必要になります。 この接続は、ストアドプロシージャまたは関数とは別のデータベースセッションにあり、異なる**SET**オプションが設定されている可能性があります。別のトランザクションに含まれているか、一時テーブルが表示されていません。 マネージド ストアド プロシージャや関数のコードが SQL Server プロセスで実行されているということは、だれかがそのサーバーに接続して、マネージド コードを呼び出す SQL ステートメントを実行したことを意味します。 ストアドプロシージャまたは関数は、その接続のコンテキストでトランザクションや**SET**オプションなどと共に実行することをお勧めします。 これを "コンテキスト接続" と呼びます。  
  
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
  
  
