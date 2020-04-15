---
title: データ ソースの使用 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], about data sources
ms.assetid: d5550619-22b2-4b16-bd08-fbabb6554c40
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df9b09e4c5519e0fff44902bd83b8e3d92a67ca8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286553"
---
# <a name="using-data-sources"></a>データ ソースの使用
データ ソースは通常、エンド ユーザーまたは技術者が*ODBC アドミニストレータ*と呼ばれるプログラムを使用して作成します。 ODBC アドミニストレーターは、ドライバーを使用するようにユーザーに求め、そのドライバーを呼び出します。 ドライバーは、データ ソースに接続するために必要な情報を要求するダイアログ ボックスを表示します。 ユーザーが情報を入力すると、ドライバーは、システムに保存します。  
  
 その後、アプリケーションは、ドライバー マネージャーを呼び出し、コンピューターのデータ ソースの名前またはファイル データ ソースを含むファイルのパスを渡します。 コンピューターのデータ ソース名が渡されると、ドライバー マネージャーは、データ ソースによって使用されるドライバーを検索するシステムを検索します。 次に、ドライバーを読み込み、データ ソース名を渡します。 ドライバーは、データ ソース名を使用して、データ ソースに接続するために必要な情報を検索します。 最後に、データ ソースに接続し、通常はユーザー ID とパスワードを要求しますが、通常は格納されません。  
  
 ファイル データ ソースが渡されると、ドライバー マネージャーは、ファイルを開き、指定されたドライバーを読み込みます。 ファイルに接続文字列も含まれている場合は、これをドライバーに渡します。 接続文字列の情報を使用して、ドライバーはデータ ソースに接続します。 接続文字列が渡されなかった場合、ドライバーは通常、必要な情報をユーザーに求めます。
