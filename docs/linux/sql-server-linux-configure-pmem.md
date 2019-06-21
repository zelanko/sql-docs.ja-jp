---
title: Linux 上の SQL Server の永続的なメモリ (PMEM) を構成する方法 |Microsoft Docs
description: この記事では、Linux で PMEM を構成するチュートリアルについては、説明します。
author: DBArgenis
ms.author: argenisf
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 5421d42933660843ac51be3d942a94cf47866200
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66713235"
---
# <a name="how-to-configure-persistent-memory-pmem-for-sql-server-on-linux"></a>Linux 上の SQL Server の永続的なメモリ (PMEM) を構成する方法

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、SQL Server on Linux の永続的なメモリ (PMEM) を構成する方法について説明します。 Linux 上の PMEM サポートは、SQL Server 2019 プレビューで導入されました。

## <a name="overview"></a>概要

SQL Server 2016 には、非揮発性の Dimm のサポートが導入され、最適化と呼ばれる[ログ キャッシュの末尾は NVDIMM に]( https://blogs.msdn.microsoft.com/bobsql/2016/11/08/how-it-works-it-just-runs-faster-non-volatile-memory-sql-server-tail-of-log-caching-on-nvdimm/)します。 これらの最適化には、永続的ストレージにログ バッファーを強化するために必要な操作の数が減少します。 これは、DAX のモードでの永続的なメモリ デバイスに直接アクセスを Windows Server を活用します。

SQL Server 2019 プレビューは、(PMEM) デバイス、Linux を永続的なメモリのサポートを拡張 PMEM 上に配置するデータとトランザクションのログ ファイルの完全な啓蒙を提供します。 効率的なユーザー領域を使用して、記憶域デバイスへのアクセスのメソッドを指す啓蒙`memcpy()`操作。 ファイル システムと記憶域スタックを通じて進行中ではなくは、SQL Server は、待機時間を短縮するデバイスにデータを直接配置する Linux 上の DAX のサポートを利用します。

## <a name="enable-enlightenment-of-database-files"></a>データベース ファイルの啓蒙を有効にします。
Linux 上の SQL server データベース ファイルの啓蒙を有効にするには、次の手順に従います。

1. デバイスを構成します。

  Linux では、使用、`ndctl`ユーティリティ。

  - インストール`ndctl`PMEM デバイスを構成します。 見つかります[ここ](https://docs.pmem.io/getting-started-guide/installing-ndctl)します。
  - [Ndctl] を使用すると、名前空間を作成します。

  ```bash 
  ndctl create-namespace -f -e namespace0.0 --mode=fsdax* --map=mem
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

  - 作成してマウント PMEM デバイス

    たとえば、XFS で

    ```bash
    mkfs.xfs -f /dev/pmem0
    mount -o dax,noatime /dev/pmem0 /mnt/dax
    xfs_io -c "extsize 2m" /mnt/dax
    ```

    たとえば、EXT4 の

    ```bash
    mkfs.ext4 -b 4096 -E stride=512 -F /dev/pmem0
    mount -o dax,noatime /dev/pmem0 /mnt/dax
    ```

  デバイスは、ndctl で構成されている、書式設定およびマウントされていますが後で、データベース ファイルを配置できます。 新しいデータベースを作成することもできます。 

1. PMEM デバイスは、O_DIRECT セーフであるために、トレース フラグを強制フラッシュ メカニズムを無効にする 3979 を有効にします。 このトレース フラグは、スタートアップ トレース フラグは、およびよう mssql conf ユーティリティを使用して有効にする必要があります。 これは、サーバー全体の構成変更をデータの整合性を保証する強制フラッシュ メカニズムが必要な O_DIRECT 非準拠デバイスがある場合に、このトレース フラグを使用する必要がありますに注意してください。 詳細について参照してください。 https://support.microsoft.com/en-us/help/4131496/enable-forced-flush-mechanism-in-sql-server-2017-on-linux

1. SQL Server を再起動してください。

## <a name="next-steps"></a>次のステップ

Linux 上の SQL Server に関する詳細については、次を参照してください。 [SQL Server on Linux](sql-server-linux-overview.md)します。
