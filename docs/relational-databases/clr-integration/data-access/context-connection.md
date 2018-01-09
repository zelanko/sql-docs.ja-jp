---
title: "コンテキスト接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f7d8583586c151eaeecf2cb4088536a0810337a6
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="context-connection"></a>コンテキスト接続
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]内部データ アクセスの問題は、非常に一般的なシナリオです。 内部データにアクセスすることは、CLR (共通言語ランタイム) ストアド プロシージャや関数を実行しているサーバーへのアクセスを考えることです。 1 つのオプションを使用して接続を作成する**System.Data.SqlClient.SqlConnection**をローカル サーバーを指す接続文字列の指定、および接続を開きます。 これには、ログインのための資格情報を指定することが必要になります。 接続がストアド プロシージャまたは関数よりも、別のデータベース セッションに、異なる場合があります**設定**別のトランザクションでは、オプションで、一時テーブルを認識しないようにします。 マネージ ストアド プロシージャや関数のコードが SQL Server プロセスで実行されているということは、だれかがそのサーバーに接続して、マネージ コードを呼び出す SQL ステートメントを実行したことを意味します。 多くの場合、ストアド プロシージャまたはそのトランザクションと共に、その接続のコンテキストで実行される関数を**設定**オプション、およびなどです。 これを "コンテキスト接続" と呼びます。  
  
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
 [正規の vs です。コンテキスト接続](../../../relational-databases/clr-integration/data-access/context-connections-vs-regular-connections.md)  
 通常の接続とコンテキスト接続の違いについて説明します。  
  
 [標準モードとコンテキスト接続に関する制限事項](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md)  
 通常の接続とコンテキスト接続の制限事項について説明します。  
  
  
