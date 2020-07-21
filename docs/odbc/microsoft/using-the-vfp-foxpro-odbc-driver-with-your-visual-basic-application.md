---
title: Visual Basic アプリケーションで VFP FoxPro ODBC ドライバーを使用する |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81292702"
---
# <a name="using-the-vfp-foxpro-odbc-driver-with-your-visual-basic-application"></a>Visual Basic アプリケーションでの VFP FoxPro ODBC ドライバーの使用
Microsoft® Visual Basic®アプリケーションは、Visual FoxPro データソースに接続するデータコントロールを作成することによって、Visual FoxPro データと通信できます。  
  
#### <a name="to-connect-to-visual-foxpro-data-using-the-data-control-in-visual-basic"></a>Visual Basic のデータコントロールを使用して Visual FoxPro データに接続するには  
  
1.  Visual FoxPro に含まれている TasTrade サンプルデータベースに接続する "test" という名前のデータソースを作成します。 既定の Visual FoxPro のインストールでは、次の場所に TasTrade サンプルデータベースが配置されます。  
  
    ```  
    c:\vfp\samples\mainsamp\data\tastrade.dbc  
    ```  
  
2.  Visual Basic で、新しいフォームを作成し、テキストボックスとデータコントロールを配置します。  
  
3.  データコントロールの Connect プロパティを次のように変更します。  
  
    ```  
    ODBC;DATABASE=tastrade;DSN=test  
    ```  
  
4.  RecordsetType プロパティを次のように変更します。  
  
    ```  
    2 - Snapshot  
    ```  
  
5.  "RecordSource" プロパティを次のように変更します。  
  
    ```  
    customer  
    ```  
  
6.  テキストボックスの DataSource プロパティを、データコントロールの既定の名前に変更します。  
  
    ```  
    data1  
    ```  
  
7.  テキストボックスの DataField プロパティを次のように変更します。  
  
    ```  
    customer_id  
    ```  
  
8.  フォームを実行し、データコントロールを使用して、Visual FoxPro TasTrade サンプルデータベースの customer id フィールドをスキップします。
