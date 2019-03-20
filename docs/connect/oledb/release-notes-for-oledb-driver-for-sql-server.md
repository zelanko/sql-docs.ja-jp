---
title: リリース ノート (OLE DB Driver for SQL Server) | Microsoft Docs
ms.date: 02/13/2019
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: genemi
author: mateusz-kmiecik
ms.author: v-makmie
ms.openlocfilehash: 2a1d6d216f4f7ec7fee0f5f9aa5810c78f1936e6
ms.sourcegitcommit: 03870f0577abde3113e0e9916cd82590f78a377c
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/18/2019
ms.locfileid: "58161769"
---
# <a name="release-notes-for-the-microsoft-ole-db-driver-for-sql-server"></a>Microsoft OLE DB Driver (SQL Server 用) のリリース ノート

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

このページでは、各バージョンの Microsoft OLE DB Driver for SQL Server に追加された内容について説明します。

<!--
USE THE TABLE FORMAT!
Hello, from now on, please use the table-based format standard for all new Release Notes content.
See section "## 18.2.1" for a live example in this article.
Thank you. For questions, contact GeneMi. (2019/03/16)
-->

## <a name="1821"></a>18.2.1

<!--
USE THE TABLE FORMAT!
Hello, from now on, please use the table-based format standard for all new Release Notes content.
See section "## 18.2.1" for a live example in this article.
Thank you. For questions, contact GeneMi. (2019/03/16)
-->

2019 年 2 月

### <a name="features-added"></a>追加された機能

| 追加された機能 | 詳細 |
| :------------ | :------ |
| サーバーの utf-8 エンコードをサポートします。 | &bull; &nbsp; [OLE DB Driver for SQL Server の UTF-8 のサポート](features/utf-8-support-in-oledb-driver-for-sql-server.md)。 |
| Azure Active Directory 認証のサポート。 | &bull; &nbsp; [Azure Active Directory の使用](features/using-azure-active-directory.md)。 |
| &nbsp; | &nbsp; |

## <a name="1810"></a>18.1.0

2018 年 7 月

### <a name="features-added"></a>追加された機能

| 追加された機能 | 詳細 |
| :------------ | :------ |
| サポート、`UseFMTONLY`接続文字列キーワード、および、`SSPROP_INIT_USEFMTONLY`初期化プロパティ。 | `UseFMTONLY` 接続するときのメタデータを取得する方法を制御[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降。<br/><br/>&bull; &nbsp; [OLE DB Driver for SQL Server での接続文字列キーワードの使用](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)。 |
| &nbsp; | &nbsp; |

### <a name="bugs-fixed"></a>修正されたバグ

| 修正されたバグ | 詳細 |
| :-------- | :------ |
| BCP フォーマット ファイルの正しくないバージョンを固定します。 | OLE DB ドライバー 18.0 正しく設定しない 18.0、BCP フォーマット ファイルのバージョンの代わりに 11.0 にします。<br/><br/>OLE DB ドライバー 18.1 は OLE DB ドライバー 18.0 によって生成されたフォーマット ファイルを読み取ることができません。<br/><br/>新しいドライバーとドライバーの以前のバージョンによって生成されたフォーマット ファイルを使用する必要がある場合、バージョン 11.0 を変更するファイルを手動で編集することができます。 |
| &nbsp; | &nbsp; |

## <a name="1802"></a>18.0.2

### <a name="features-added"></a>追加された機能

| 追加された機能 | 詳細 |
| :------------ | :------ |
| サポート、`MultiSubnetFailover`接続文字列キーワード、および`SSPROP_INIT_MULTISUBNETFAILOVER`初期化プロパティ。 | &bull; &nbsp; [OLE DB Driver for SQL Server の高可用性、ディザスター リカバリーに関するサポート](features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)。<br/><br/>&bull; &nbsp; [OLE DB Driver for SQL Server での接続文字列キーワードの使用](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)。 |
| &nbsp; | &nbsp; |

## <a name="see-also"></a>参照

[Microsoft OLE DB Driver for SQL Server](oledb-driver-for-sql-server.md)
