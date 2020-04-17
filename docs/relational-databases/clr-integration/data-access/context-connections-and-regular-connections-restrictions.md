---
title: 通常の接続とコンテキスト接続に関する制限 |マイクロソフトドキュメント
description: この資料では、コンテキストと通常の接続を介して Microsoft SQL Server プロセスで実行されるコードに関連する制限について説明します。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: 0c6fe4cb-d846-40b5-8884-35a9c770f5e8
author: rothja
ms.author: jroth
ms.openlocfilehash: fac92658366cceffc3d4fac5ba650f9a14501185
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81485343"
---
# <a name="context-connections-and-regular-connections---restrictions"></a>コンテキスト接続と通常の接続 - 制限
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このトピックでは、コンテキストと通常の接続を通じてプロセス[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]で実行されるコードに関連する制限について説明します。  
  
## <a name="restrictions-on-context-connections"></a>コンテキスト接続に関する制限事項  
 アプリケーションを開発するときは、コンテキスト接続に適用される次の制限事項を考慮してください。  
  
-   特定の接続に対して特定の時点に開くことができるコンテキスト接続は 1 つだけです。 複数のステートメントをそれぞれ独立した接続で同時に実行する場合、その中の 1 つの接続しか独自のコンテキスト接続を取得できません。 この制限事項は、異なる接続からの同時実行要求には影響しません。つまり、特定の接続の特定の要求にしか影響しません。  
  
-   コンテキスト接続では、MARS (複数のアクティブな結果セット) がサポートされません。  
  
-   クラス**は**コンテキスト接続では動作しません。  
  
-   コンテキスト接続では、更新バッチ処理がサポートされません。  
  
-   コンテキスト接続に対して実行されるコマンドでは **、SqlNotificationRequest**を使用できません。  
  
-   コンテキスト接続に対して実行しているコマンドはキャンセルできません。 メソッド**は**、要求を無視せずに通知を受け取ります。  
  
-   "context connection=true" を使用する場合は、他の接続文字列キーワードを使用できません。  
  
-   プロパティ**は**、インスタンスの名前ではなく **、SqlConnection**の接続文字列が "コンテキスト接続=true" の場合に null を返[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。  
  
-   **プロパティを**設定しても、コンテキスト接続に対してコマンドが実行されるときは何の影響もありません。  
  
## <a name="restrictions-on-regular-connections"></a>通常の接続に関する制限事項  
 アプリケーションを開発するときは、通常の接続に適用される次の制限事項を考慮してください。  
  
-   内部サーバーに対する非同期コマンドの実行はサポートされません。 コマンドの接続文字列に "async=true" を含めて、コマンドを実行すると **、System.NotSupportedException**がスローされます。 このメッセージは、"プロセス内で実行されている場合、非同期処理[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]はサポートされていません。  
  
-   **Sql 依存関係**オブジェクトはサポートされていません。  
  
## <a name="see-also"></a>参照  
 [コンテキスト接続](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
