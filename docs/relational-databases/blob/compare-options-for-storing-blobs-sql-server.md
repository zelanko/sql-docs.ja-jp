---
title: Blob (SQL Server) を保存するオプションの比較 | Microsoft Docs
description: SQL Server では、Windows アプリケーションで使用されるバイナリ ラージ オブジェクト (BLOB) データを格納できます。 非構造化データを格納するために、このリレーショナル データベースのオプションを比較します。
ms.custom: ''
ms.date: 03/04/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
ms.assetid: 6038697b-36a9-49e8-a02a-2ad9e2e60e5a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 049e001d5193f1d96862755e8045bb84d002050d
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/09/2020
ms.locfileid: "83000090"
---
# <a name="compare-options-for-storing-blobs-sql-server"></a>Blob (SQL Server) を保存するオプションの比較

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

ファイルおよびドキュメントを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に格納するために使用できるオプションを説明して比較します。

## <a name="storing-files-in-the-database---benefits-and-expectations"></a><a name="Expectations"></a> データベースへのファイルの格納 - 利点と予測

企業データの大部分は、実際は構造化されておらず、通常、ファイルや文書としてファイル システムに保存されています。 このデータの大半は、Windows API を通じてファイルにアクセスするアプリケーションによって作成、管理、および使用されます。 通常、企業はこのデータをファイル システムに保存し、ファイルの関連するメタデータ ファイルをリレーショナル データベースに格納します。

非構造化データをリレーショナル データベースに統合すると、次の利点があります。

- バックアップなどの、統合ストレージおよびデータ管理機能。
- データとメタデータ全体に対するフルテキスト検索、セマンティック検索などの統合サービス。
- 非構造化データの管理およびポリシーの管理の容易さ。

一般に非構造化データをリレーショナル データベースに格納するのは不便でした。 確立されているアプリケーション (Microsoft Word、Adobe Reader など) でリレーショナル データベース API を操作するのは実用的ではありませんでした。 このようなアプリケーションでは、データが Windows API を通じてアクセスされることが前提となっています。 アプリケーションでは次のことが前提となります。

- Windows アプリケーションにはデータベース トランザクションが不要であり、認識もされない。
- Windows アプリケーションは、ファイルおよびディレクトリ データのためにファイル システム API との互換性が必要。

何年か前は、SQL Server ではリレーショナル データベースに非構造化データを格納するさまざまな方法が提供されませんでした。 しかし、最近では非構造化データを格納する方法が提供されます。

## <a name="filestream"></a><a name="Filestream"></a> FILESTREAM

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には既に FILESTREAM 機能があります。 FILESTREAM 機能では、ファイル システムでファイルとして格納される非構造化データの効率的な保管、管理、およびストリーミングを行うことができます。 ただし、FILESTREAM ソリューションはカスタム プログラミングを必要とし、上で説明した完全な Windows アプリケーションの互換性の要件を満たしていません。

## <a name="filetables"></a><a name="FileTables"></a> FileTables

FileTable 機能は、既存の FILESTREAM 機能をベースとして構築されています。 FileTable 機能により、企業では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースで、非構造化ファイル データ、およびディレクトリ階層を格納することができます。 この機能によって、ファイルベース データの Windows アプリケーションの互換性や非トランザクション アクセスの要件に対応できます。

## <a name="comparing-filestream-and-filetable"></a><a name="CompareFileTable"></a> FILESTREAM と FileTable の比較

|機能|ファイル サーバーとデータベース ソリューション|FILESTREAM ソリューション|FileTable ソリューション|
|:------|:--------------------------------|:------------------|:-----------------|
|**管理タスクのシングル ストーリー**|いいえ|はい|**はい**|
|**サービスの単一セット**: 検索、レポート、クエリなど|いいえ|はい|**はい**|
|**統合セキュリティ モデル**|いいえ|はい|**はい**|
|**FILESTREAM データのインプレース更新**|はい|いいえ|**はい**|
|**データベースで管理されるファイルおよびディレクトリの階層**|いいえ|いいえ|**はい**|
|**Windows アプリケーションの互換性**|はい|いいえ|**はい**|
|**ファイルの属性へのリレーショナル アクセス**|いいえ|いいえ|**はい**|

## <a name="comparing-filestream-and-remote-blob-store-rbs"></a><a name="CompareRBS"></a> FILESTREAM とリモート BLOB ストア (RBS) の比較

非構造化データを格納するためのもう 1 つのオプションには、リモート BLOB ストア (RBS) が含まれます。 詳細については、「[Remote Blob Store (RBS) (SQL Server)](remote-blob-store-rbs-sql-server.md)」 (リモート BLOB ストア (RBS) (SQL Server)) を参照してください。

## <a name="more-information"></a><a name="more"></a> その他の情報

[FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)  
[FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md)  
[リモート BLOB ストア &#40;RBS&#41; &#40;SQL Server&#41;](../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)
