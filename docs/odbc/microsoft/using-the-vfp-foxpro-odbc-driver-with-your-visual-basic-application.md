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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 017e8e7897b2b792d7a864dc336537d76dcad8b9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68087985"
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
