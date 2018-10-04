---
title: 高速解析の設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: dcd1dc09-6eaf-440b-9ce6-fef779ff794f
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 960876737e552e7c5a9af75cc23d7e43e3799735
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48170612"
---
# <a name="set-fast-parse"></a>高速解析を設定する
  高速解析を使用するフラット ファイル ソースまたはデータ変換の変換の列ごとに、高速解析プロパティを設定する必要があります。 プロパティを設定するには、フラット ファイル ソースおよびデータ変換の変換の詳細エディターを使用します。  
  
### <a name="to-set-fast-parse"></a>高速解析を設定するには  
  
1.  フラット ファイル ソースまたはデータ変換の変換を右クリックし、 **[詳細エディターの表示]** をクリックします。  
  
2.  **[詳細エディター]** ダイアログ ボックスの **[入力プロパティと出力プロパティ]** タブをクリックします。  
  
3.  **[入力および出力]** ペインで、高速解析を有効にする列をクリックします。  
  
4.  [プロパティ] ウィンドウで、展開、**カスタム プロパティ**ノード、および設定して、`FastParse`プロパティを`True`します。  
  
5.  **[OK]** をクリックします。  
  
  
