---
title: Azure BLOB Source | Microsoft Docs
ms.custom: ''
ms.date: 07/25/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpblobsrc.f1
- sql14.dts.designer.afpblobsrc.f1
ms.assetid: 80645c5c-88c8-4fb0-8607-de1bb7bffcbb
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b00b3fbfeeff2fa7c99ac8f69e3c46c79e4ed796
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35334706"
---
# <a name="azure-blob-source"></a>Azure BLOB Source
  **Azure BLOB Source** コンポーネントは、SSIS パッケージが Azure BLOB のデータを読み取ることを可能にします。 サポートされるファイル形式は、CSV および AVRO です。
  
  Azure BLOB Source のエディターを表示するには、データ フロー デザイナー上に **Azure Blob Source** をドラッグ アンド ドロップし、これをダブルクリックしてエディターを開きます。  
  
 **Azure BLOB Source** は、[SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) のコンポーネントです。  
  
1.  **[Azure storage connection manager]** (Azure Storage 接続マネージャー) フィールドに、既存の Azure Storage 接続マネージャーを指定するか、または Azure Storage アカウントを参照する新しい Azure Storage 接続マネージャーを作成します。  
  
2.  **[Blob container name]** (BLOB コンテナー名) フィールドに、ソース ファイルを含む BLOB コンテナーの名前を指定します。  
  
3.  **[Blob name]** (BLOB 名) フィールドに、BLOB のパスを指定します。  
  
4.  **[Blob file format]** (BLOB ファイル形式) フィールドに、使用する形式を指定します。  
  
5.  CSV 形式の場合は、 **[Column delimiter character]** (列区切り文字) に値を指定する必要があります。 さらに、ファイルの 1 行目に列名が含まれている場合は、 **[先頭データ行を列名として使用する]** も指定する必要があります。  
  
6.  接続情報を指定した後、 **[列]** ページで、SSIS データ フローのマップ元の列をマップ先の列にマップします。  
  
  
