---
title: Azure Blob Destination | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobdest.f1
- sql11.dts.designer.afpblobdest.f1
ms.assetid: 820a1e7a-7182-4c7b-ab56-5b4097a7e042
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7e20e18f2e4395720c4e895d53c9a78a75d38dee
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62828268"
---
# <a name="azure-blob-destination"></a>Azure Blob Destination
  **Azure Blob Destination** コンポーネントは、SSIS パッケージが Azure Blob にデータを書き込めるようにします。 サポートされるファイル形式は、CSV および AVRO です。 **Azure Blob Destination**をデータフローデザイナーにドラッグアンドドロップし、ダブルクリックしてエディターを表示します。  
  
1.  **[Azure storage connection manager]** (Azure Storage 接続マネージャー) フィールドに、既存の Azure Storage 接続マネージャーを指定するか、または Azure Storage アカウントを参照する新しい Azure Storage 接続マネージャーを作成します。  
  
2.  **[Blob container name]** (BLOB コンテナー名) フィールドに、ソース ファイルを含む BLOB コンテナーの名前を指定します。  
  
3.  **[Blob name]** (BLOB 名) フィールドに、BLOB のパスを指定します。  
  
4.  **[Blob file format]** (BLOB ファイル形式) フィールドに、使用する形式を指定します。  
  
5.  CSV 形式の場合は、 **[Column delimiter character]** (列区切り文字) に値を指定する必要があります。 また、ファイルの最初の行に列名が含まれている場合は、**最初のデータ行で列名**を選択します。  
  
6.  接続情報を指定した後、 **[列]** ページで、SSIS データ フローのマップ元の列をマップ先の列にマップします。  
  
  
