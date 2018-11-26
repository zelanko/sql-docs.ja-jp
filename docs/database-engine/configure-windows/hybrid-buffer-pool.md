---
title: ハイブリッド バッファー プール | Microsoft Docs
ms.custom: ''
ms.date: 11/06/2018
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ''
author: DBArgenis
ms.author: argenisf
manager: craigg
ms.openlocfilehash: a8098c38b72ba44ab973fe5564b93740252bafc6
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2018
ms.locfileid: "51560309"
---
# <a name="hybrid-buffer-pool"></a>ハイブリッド バッファー プール
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server 2019 CTP 2.1 では、SQL Server データベースに新機能が導入されており、これにより、永続メモリ (PMEM) デバイスに格納されているデータベース ファイルのデータ ページに直接アクセスできるようになります。 

永続メモリのない従来のシステムでは、SQL Server によってデータ ページがバッファー プールにキャッシュされます。 ハイブリッド バッファー プールを使用すると、SQL Server では、バッファー プールの DRAM ベースの部分にページのコピーを実行することをスキップし、代わりに PMEM デバイスにあるデータベース ファイル上で直接ページを参照します。 ハイブリッド バッファー プールのための PMEM にあるデータ ファイルへのアクセスは、メモリ マップ I/O (エンライトンメントとも呼ばれる) を使用して実行されます。

PMEM デバイスで直接参照できるのは、クリーン ページのみです。 ページがダーティになると、そのページは DRAM に保持され、最終的に PMEM デバイスに書き込まれます。

この機能は、Windows と Linux の両方で使用できます。

## <a name="enable-hybrid-buffer-pool"></a>ハイブリッド バッファー プールの有効化

CTP 2.1 では、ハイブリッド バッファー プールを使用するために、スタートアップ トレース フラグ 809 を有効にする必要があります。

## <a name="best-practices-for-hybrid-buffer-pool"></a>ハイブリッド バッファー プールのベスト プラクティス

* Windows 上でご利用の PMEM デバイスをフォーマットする場合、NTFS に利用できる最大のアロケーション ユニット サイズ (Windows Server 2019 では 2 MB) を使用して、デバイスが DAX (DirectAccess) に対して有効にされていることを確認します
  