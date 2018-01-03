---
title: "データ プロバイダー |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data providers [ADO]
- OLE DB providers [ADO]
- ADO, OLE DB providers
ms.assetid: 877b9f25-60c4-4ab6-8052-2c28a3849e89
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b424a116282c7c1edcfa06f22fc72f32a7e0fcda
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="data-providers"></a>データ プロバイダー
データ プロバイダーは、SQL データベース、インデックス付きのシーケンシャル ファイル、スプレッドシート、ドキュメント ストア、およびメール ファイルなどのデータのさまざまなソースを表します。 プロバイダーは、均等に行セットと呼ばれる共通の抽象化を使用してデータを公開します。  
  
 ADO では強力で柔軟ないくつかの別のデータ プロバイダーのいずれかに接続し、指定されたプロバイダーの特定の機能に関係なく、同じプログラミング モデルを公開します。 ただし、各データ プロバイダーが一意であるため、アプリケーションが ADO とやり取りする方法によって異なりますデータ プロバイダー。  
  
 機能と、OLE DB Provider for Microsoft SQL Server データベースへのアクセスに使用される、SQL Server の機能が大きく異なるため、Microsoft OLE DB Provider for Internet Publishing ファイルへのアクセスに使用されるものはたとえば、Web サーバーに保存します。
