---
title: Linux 上の SQL Server の永続的なメモリ (PMEM) を構成する方法 |Microsoft Docs
description: この記事では、Linux で PMEM を構成するチュートリアルについては、説明します。
author: DBArgenis
ms.author: argenisf
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 71c4af08573f54b5a33a95f0c821dfdb81b4f0a0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47765596"
---
# <a name="how-to-configure-persistent-memory-pmem-for-sql-server-on-linux"></a>Linux 上の SQL Server の永続的なメモリ (PMEM) を構成する方法

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、SQL Server on Linux の永続的なメモリ (PMEM) を構成する方法について説明します。 Linux 上の PMEM サポートは、SQL Server 2019 CTP 2.0 で導入されました。

## <a name="overview"></a>概要

SQL Server 2016 には、非揮発性の Dimm のサポートが導入され、最適化と呼ばれる[ログ キャッシュの末尾は NVDIMM に]( https://blogs.msdn.microsoft.com/bobsql/2016/11/08/how-it-works-it-just-runs-faster-non-volatile-memory-sql-server-tail-of-log-caching-on-nvdimm/)永続的ストレージにログ バッファーを強化するために必要な操作の量を短縮します。 これは、DAX のモードでの永続的なメモリ デバイスに直接アクセスする Windows Server の機能を活用します。

SQL Server 2019 プレビューは、(PMEM) デバイス、Linux を永続的なメモリのサポートを拡張 PMEM 上に配置するデータとトランザクションのログ ファイルの完全な啓蒙を提供します。 啓蒙は効率的なユーザー スペース memcpy 操作を使用して、記憶域デバイスへのアクセスのメソッドを表します。 はなくファイル システムと記憶域スタックを SQL Server の移動が直接データを最小限の待機時間をかけずに、デバイスに配置する Linux 上の DAX サポートを利用します。

## <a name="enable-enlightenment-of-database-files"></a>データベース ファイルの啓蒙を有効にします。
Linux 上の SQL server データベース ファイルの啓蒙を有効にするには、次の手順に従います。

1. Linux でのデバイスを構成を使用してこれが実行される、`ndctl`ユーティリティ。

  - インストールのインストール`ndctl`pmem デバイスを構成します。 見つかります[ここ](https://docs.pmem.io/getting-started-guide/installing-ndctl)します。
  - [Ndctl] を使用すると、名前空間を作成します。

  ```bash 
  ndctl create-namespace -f -e namespace0.0 --mode=fsdax* –map=mem
  ```

  >[!NOTE]
  >使用する場合`ndctl`59 を使用してよりも低いバージョン`--mode=memory`します。

  使用`ndctl`を名前空間を確認します。 サンプル出力が次に示します。

```bash
ndctl list
[
  {
    "dev":"namespace0.0",
    "mode":"memory",
    "size":1099511627776,
    "blockdev":"pmem0",
    "numa_node":0
  }
]
```

  - 作成してマウント pmem デバイス

    たとえば、XFS で

    ```bash
    mkfs.xfs -f /dev/pmem0
    mount –o dax,noatime /dev/pmem0 /mnt/dax
    xfs_io -c "extsize 2m" /mnt/dax
    ```

    たとえば、EXT4 の

    ```bash
    mkfs.ext4 -b 4096 -E stride=512 -F /dev/pmem0
    mount –o dax,noatime /dev/pmem0 /mnt/dax
    ```

  デバイスは、ndctl で構成されている、書式設定およびマウントされていますが後で、データベース ファイルを配置できます。 新しいデータベースを作成することもできます。 

1. トレース フラグ 3979 を使用して SQL Server データベース ファイル啓蒙を有効にします。 このトレース フラグは、スタートアップ トレース フラグは、およびよう mssql conf ユーティリティを使用して有効にする必要があります。

1. SQL Server を再起動してください。

## <a name="next-steps"></a>次の手順

Linux 上の SQL Server に関する詳細については、次を参照してください。 [SQL Server on Linux](sql-server-linux-overview.md)します。
