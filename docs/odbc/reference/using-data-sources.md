---
title: データ ソースの使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data sources [ODBC], about data sources
ms.assetid: d5550619-22b2-4b16-bd08-fbabb6554c40
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 06331bd28b372c388cd2c4cba9576345408d113f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="using-data-sources"></a>データ ソースを使用します。
プログラムによる技術者と呼ばれるまたはデータ ソースは、エンド ユーザーによって作成された通常の*ODBC アドミニストレーター*です。 ODBC 管理者は、ドライバーを使用するユーザーを要求し、そのドライバーを呼び出します。 ドライバーでは、データ ソースへの接続に必要な情報を要求するダイアログ ボックスが表示されます。 情報を入力すると、後に、ドライバーは、システムでそれを格納します。  
  
 その後、アプリケーションでは、ドライバー マネージャーを呼び出しし、コンピューターのデータ ソースの名前またはファイル データ ソースを含むファイルのパスに渡します。 マシンのデータ ソース名が渡された場合、ドライバー マネージャーは、データ ソースによって使用されているドライバーを検索するシステムを検索します。 ドライバーを読み込み、データ ソース名を渡します。 ドライバーでは、データ ソース名を使用して、データ ソースへの接続に必要な情報を見つけます。 最後に、通常、ユーザー ID とパスワードの一般的に保存されていないユーザーに確認、データ ソースに接続します。  
  
 ファイル データ ソースが渡された場合、ドライバー マネージャーはファイルを開き、指定されたドライバーを読み込みます。 ファイルには、接続文字列も含まれている場合、ドライバーをこのに渡します。 接続文字列に情報を使用して、ドライバーは、データ ソースに接続します。 接続文字列が渡されなかった場合、ドライバーは一般にユーザーに必要な情報を求めます。
