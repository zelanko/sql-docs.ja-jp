---
title: 高速解析の設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: dcd1dc09-6eaf-440b-9ce6-fef779ff794f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7d41b15325586733ab54a37f4c3f007ce0253eaf
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66055823"
---
# <a name="set-fast-parse"></a>高速解析を設定する
  高速解析を使用するフラット ファイル ソースまたはデータ変換の変換の列ごとに、高速解析プロパティを設定する必要があります。 プロパティを設定するには、フラット ファイル ソースおよびデータ変換の変換の詳細エディターを使用します。  
  
### <a name="to-set-fast-parse"></a>高速解析を設定するには  
  
1.  フラット ファイル ソースまたはデータ変換の変換を右クリックし、 **[詳細エディターの表示]** をクリックします。  
  
2.  **[詳細エディター]** ダイアログ ボックスの **[入力プロパティと出力プロパティ]** タブをクリックします。  
  
3.  **[入力および出力]** ペインで、高速解析を有効にする列をクリックします。  
  
4.  プロパティウィンドウで、[**カスタムプロパティ**] ノードを展開し、 `FastParse`プロパティをに`True`設定します。  
  
5.  **[OK]** をクリックします。  
  
  
