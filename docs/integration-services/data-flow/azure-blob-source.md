---
title: Azure BLOB Source | Microsoft Docs
ms.custom: ''
ms.date: 08/20/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpblobsrc.f1
- sql14.dts.designer.afpblobsrc.f1
ms.assetid: 80645c5c-88c8-4fb0-8607-de1bb7bffcbb
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 62d4cc21bbe5469886e4087c9ec310abc9185ed8
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2019
ms.locfileid: "58282075"
---
# <a name="azure-blob-source"></a>Azure BLOB Source
  **Azure BLOB Source** コンポーネントは、SSIS パッケージが Azure BLOB のデータを読み取ることを可能にします。 サポートされるファイル形式は、CSV と AVRO です。
  
  Azure BLOB Source のエディターを表示するには、データ フロー デザイナー上に **Azure Blob Source** をドラッグ アンド ドロップし、これをダブルクリックしてエディターを開きます。  
  
 **Azure BLOB Source** は、[SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) のコンポーネントです。  
  
1.  **[Azure storage connection manager]** (Azure Storage 接続マネージャー) フィールドに、既存の Azure Storage 接続マネージャーを指定するか、または Azure Storage アカウントを参照する新しい Azure Storage 接続マネージャーを作成します。  
  
2.  **[Blob container name]** (BLOB コンテナー名) フィールドに、ソース ファイルを含む BLOB コンテナーの名前を指定します。  
  
3.  **[Blob name]** (BLOB 名) フィールドに、BLOB のパスを指定します。  
  
4.  **[BLOB ファイル形式]** フィールドで、使用する BLOB 形式 (**[テキスト]** または **[Avro]**) を選択します。  
  
5.  ファイル形式が **[テキスト]** の場合は、**[列の区切り文字]** に値を指定する必要があります。 (複数の文字による区切り記号はサポートされません)。

    さらに、ファイルの 1 行目に列名が含まれている場合は、 **[先頭データ行を列名として使用する]** も指定する必要があります。

6.  ファイルが圧縮されている場合は、**[Decompress the file]** (ファイルの圧縮解除) を選択します。

7.  ファイルが圧縮されている場合は、**[圧縮の種類]** として次のいずれかを選択します: **[GZIP]**、**[DEFLATE]**、**[BZIP2]**。 Zip 形式はサポートされていません。
  
8.  接続情報を指定した後、**[列]** ページで、SSIS データ フローのマップ元の列をマップ先の列にマップします。  
  
  
