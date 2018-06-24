---
title: 高速解析を設定 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dcd1dc09-6eaf-440b-9ce6-fef779ff794f
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 94f4fe123cb37e60e175ad39b932e61376e217b8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073776"
---
# <a name="set-fast-parse"></a>高速解析を設定する
  高速解析を使用するフラット ファイル ソースまたはデータ変換の変換の列ごとに、高速解析プロパティを設定する必要があります。 プロパティを設定するには、フラット ファイル ソースおよびデータ変換の変換の詳細エディターを使用します。  
  
### <a name="to-set-fast-parse"></a>高速解析を設定するには  
  
1.  フラット ファイル ソースまたはデータ変換の変換を右クリックし、 **[詳細エディターの表示]** をクリックします。  
  
2.  **[詳細エディター]** ダイアログ ボックスの **[入力プロパティと出力プロパティ]** タブをクリックします。  
  
3.  **[入力および出力]** ペインで、高速解析を有効にする列をクリックします。  
  
4.  [プロパティ] ウィンドウで、展開、**カスタム プロパティ**ノードを展開し、セット、`FastParse`プロパティを`True`です。  
  
5.  **[OK]** をクリックします。  
  
  