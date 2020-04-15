---
title: Visual Basic アプリケーションで VFP FoxPro ODBC ドライバを使用する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], visual basic applications
- Visual Basic applications [ODBC]
- FoxPro ODBC driver [ODBC], visual basic applications
- Visual FoxPro data [ODBC], visual basic applications
ms.assetid: 5223ca23-5df6-4ebc-aa3b-70682ff27a8c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 871c392166fa2f5726e6f9e8651bf758dc144a00
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292702"
---
# <a name="using-the-vfp-foxpro-odbc-driver-with-your-visual-basic-application"></a>Visual Basic アプリケーションでの VFP FoxPro ODBC ドライバーの使用
Microsoft ® Visual Basic® アプリケーションは、Visual FoxPro データ ソースに接続するデータ コントロールを作成することで、Visual FoxPro データと通信できます。  
  
#### <a name="to-connect-to-visual-foxpro-data-using-the-data-control-in-visual-basic"></a>ビジュアル 基本のデータ コントロールを使用してビジュアル フォックス プロ のデータに接続するには  
  
1.  Visual FoxPro に含まれる TasTrade サンプル データベースに接続する "test" という名前のデータ ソースを作成します。 デフォルトの Visual FoxPro インストールでは、TasTrade サンプル データベースが次の場所に配置されます。  
  
    ```  
    c:\vfp\samples\mainsamp\data\tastrade.dbc  
    ```  
  
2.  Visual Basic で、新しいフォームを作成し、テキスト ボックスとデータ コントロールを配置します。  
  
3.  次のように、データ コントロールの Connect プロパティを変更します。  
  
    ```  
    ODBC;DATABASE=tastrade;DSN=test  
    ```  
  
4.  プロパティを次のように変更します。  
  
    ```  
    2 - Snapshot  
    ```  
  
5.  プロパティを次のように変更します。  
  
    ```  
    customer  
    ```  
  
6.  テキスト ボックスの DataSource プロパティを、データ コントロールの既定の名前に変更します。  
  
    ```  
    data1  
    ```  
  
7.  テキスト ボックスの DataField プロパティを次のように変更します。  
  
    ```  
    customer_id  
    ```  
  
8.  フォームを実行し、データ コントロールを使用して、Visual FoxPro TasTrade サンプル データベースから顧客 ID フィールドをスキップします。
