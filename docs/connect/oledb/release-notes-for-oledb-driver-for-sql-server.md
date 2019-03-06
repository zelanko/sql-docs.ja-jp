---
title: リリース ノート (OLE DB Driver for SQL Server) | Microsoft Docs
ms.date: 02/12/2019
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daveng
ms.openlocfilehash: 36dc1b7325265da6231b75e9f4db46854b0b219f
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744362"
---
# <a name="release-notes-for-the-microsoft-ole-db-driver-for-sql-server"></a>Microsoft OLE DB Driver for SQL Server のリリース ノート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

このページでは、各バージョンの Microsoft OLE DB Driver for SQL Server に追加された内容について説明します。

## <a name="whats-new-in-version-1821"></a>バージョン 18.2.1 の新機能

**追加された機能:**

* サーバーの utf-8 エンコードをサポートします。 詳細については、次を参照してください。: [OLE DB Driver for SQL Server での utf-8 サポート](features/utf-8-support-in-oledb-driver-for-sql-server.md)します。
* Azure Active Directory 認証のサポート。 詳細については、「[Azure Active Directory の使用](features/using-azure-active-directory.md)」をご覧ください。

## <a name="whats-new-in-version-1810"></a>バージョン 18.1.0 の新機能

**追加された機能:**

* サポート`UseFMTONLY`接続文字列キーワードと`SSPROP_INIT_USEFMTONLY`初期化プロパティ。
`UseFMTONLY` 接続するときのメタデータを取得する方法を制御[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降。  
詳細については、以下をご覧ください。
  * [OLE DB Driver for SQL Server での接続文字列キーワードの使用](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)

**修正されたバグ:**

* BCP フォーマット ファイルの正しくないバージョンを固定します。 OLE DB ドライバー 18.0 で設定する 11.0 ではなく 18.0 BCP フォーマット ファイルのバージョン OLE DB ドライバー 18.1 は OLE DB ドライバー 18.0 によって生成されたフォーマット ファイルを読み取ることができません。 新しいドライバーとドライバーの以前のバージョンによって生成されたフォーマット ファイルを使用する必要がある場合、バージョン 11.0 を変更するファイルを手動で編集することができます。

## <a name="whats-new-in-version-1802"></a>バージョン 18.0.2 の新機能

**追加された機能**:

* サポート`MultiSubnetFailover`接続文字列キーワードと`SSPROP_INIT_MULTISUBNETFAILOVER`初期化プロパティ。  
詳細については、以下をご覧ください。  
  * [OLE DB Driver for SQL Server の高可用性、ディザスター リカバリーに関するサポート](features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)  
  * [OLE DB Driver for SQL Server での接続文字列キーワードの使用](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)

## <a name="see-also"></a>参照
[Microsoft OLE DB Driver for SQL Server](oledb-driver-for-sql-server.md)
