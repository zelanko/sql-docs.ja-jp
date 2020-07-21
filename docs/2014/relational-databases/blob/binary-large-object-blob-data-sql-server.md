---
title: バイナリ ラージ オブジェクト (Blob) データ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], design and implementation
ms.assetid: 97509274-c3f8-43e5-a37c-52f1ffe0961a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a663dedf34d75a21ee8df6b97979548c04abf7ff
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84955832"
---
# <a name="binary-large-object-blob-data-sql-server"></a>バイナリ ラージ オブジェクト (Blob) データ (SQLServer)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、ファイルおよびドキュメントをデータベースまたはリモート ストレージ デバイスに格納するためのソリューションが用意されています。  
  
##  <a name="in-this-section"></a><a name="section"></a> トピックの内容  
 [BLOB の保存オプションの比較 &#40;SQL Server&#41;](compare-options-for-storing-blobs-sql-server.md)  
 FILESTREAM、FileTable、およびリモート BLOB ストアの利点を比較します。  
  
 [FILESTREAM &#40;SQL Server&#41;](filestream-sql-server.md)  
 FILESTREAM を使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ベースのアプリケーションで非構造化データ (ドキュメントやイメージなど) をファイル システムに格納できます。 これにより、ファイル システムの豊富なストリーミング API と高いパフォーマンスをアプリケーションで活用できるほか、非構造化データとそれに対応する構造化データの間でトランザクションの一貫性も維持されます。  
  
 [FileTables &#40;SQL Server&#41;](filetables-sql-server.md)  
 FileTable 機能は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に格納されているファイル データに対して Windows ファイル名前空間のサポートと Windows アプリケーションとの互換性を提供します。 FileTable により、アプリケーションは、ストレージとデータ管理コンポーネントを統合し、非構造化データおよびメタデータに対する統合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス (フルテキスト検索、セマンティック検索など) を提供できます。  
  
 つまり、ファイルおよびドキュメントを FileTable と呼ばれる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の特殊なテーブルに保存しておき、ファイル システムに格納されているかのように、Windows アプリケーションからこれらのファイルおよびドキュメントにアクセスできるということです。このとき、クライアント アプリケーションに変更を加える必要はありません。  
  
 [リモート BLOB ストア &#40;RBS&#41; &#40;SQL Server&#41;](remote-blob-store-rbs-sql-server.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のリモート BLOB ストア (RBS) を使用すると、データベース管理者は、バイナリ ラージ オブジェクト (BLOB) を、直接サーバーに格納するのではなく、汎用的なストレージ ソリューションに格納できます。 これにより、容量を大幅に節約でき、コストのかかるサーバー ハードウェア リソースの浪費を回避できます。 RBS では、アプリケーションが BLOB データにアクセスするための標準化されたモデルを定義する一連の API ライブラリが提供されます。 また、RBS には、リモート BLOB データの管理に役立つメンテナンス ツール (ガベージ コレクションなど) も用意されています。  
  
 RBS は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール メディアに含まれていますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ プログラムではインストールされません。  
  
  
