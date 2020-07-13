---
title: OLE DB Driver のリリース ノート
description: このリリース ノート記事では、Microsoft OLE DB Driver for SQL Server の各リリースにおける変更点について説明します。
ms.date: 02/27/2020
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: genemi
author: mateusz-kmiecik
ms.author: v-makmie
ms.openlocfilehash: 70f3239f1e644850bc391a0be5ef8918e1e9e617
ms.sourcegitcommit: 66407a7248118bb3e167fae76bacaa868b134734
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "81727972"
---
# <a name="release-notes-for-the-microsoft-ole-db-driver-for-sql-server"></a>Microsoft OLE DB Driver for SQL Server のリリース ノート

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

このページでは、Microsoft OLE DB Driver for SQL Server の各バージョンで追加された内容について説明します。

<!--
USE THE TABLE FORMAT!
Hello, from now on, please use the table-based format standard for all new Release Notes content.
See section "## 18.2.1" for a live example in this article.
Thank you. For questions, contact GeneMi. (2019/03/16)
-->

## <a name="1830"></a>18.3.0

![ダウンロード](../../ssms/media/download-icon.png) [x64 インストーラーのダウンロード](https://go.microsoft.com/fwlink/?linkid=2117515)  
![ダウンロード](../../ssms/media/download-icon.png) [x86 インストーラーのダウンロード](https://go.microsoft.com/fwlink/?linkid=2117517)  

リリース日:2019 年 10 月

自動的に検出されたもの以外の言語でインストーラーをダウンロードする必要がある場合は、以下の直接リンクを使用できます。  
X64 ドライバーの場合: [簡体中国語](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x804) | [繁体中国語](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x40a)  
X86 ドライバーの場合: [簡体中国語](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x804) | [繁体中国語](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x40a)  

### <a name="features-added"></a>追加された機能

| 追加された機能 | 詳細 |
| :------------ | :------ |
| Azure Active Directory 認証のサポート (`ActiveDirectoryInteractive`、`ActiveDirectoryMSI`)。 | [Azure Active Directory の使用](features/using-azure-active-directory.md)。 |
| Azure Active Directory 認証ライブラリ (adal.dll) をインストーラーに含める | 基本ドライバーのインストールに含まれるようになりました。これにより、OLE DB インストーラーを使用すると、SQL Server 用の Microsoft Active Directory 認証ライブラリの既存のインストールがアップグレードされ、Windows のインストール済みアプリケーションの一覧からこれが削除されます。 |
| &nbsp; | &nbsp; |

### <a name="bugs-fixed"></a>修正されたバグ

| 修正されたバグ | 詳細 |
| :-------- | :------ |
| [IIndexDefinition::DropIndex](https://go.microsoft.com/fwlink/?linkid=2106448) のインデックスの削除ロジックが修正されました。 | 以前のバージョンの OLE DB ドライバーでは、インデックスの所有者のスキーマ ID とユーザー ID が同じでない場合、主キー インデックスを削除できません。 |
| &nbsp; | &nbsp; |

## <a name="previous-releases"></a>以前のリリース

以前のバージョンの OLE DB Driver をダウンロードするには、次のセクションのダウンロード リンクをクリックします。

## <a name="1823"></a>18.2.3

![ダウンロード](../../ssms/media/download-icon.png) [x64 インストーラーのダウンロード](https://go.microsoft.com/fwlink/?linkid=2119554)  
![ダウンロード](../../ssms/media/download-icon.png) [x86 インストーラーのダウンロード](https://go.microsoft.com/fwlink/?linkid=2119738)  

リリース日:2019 年 6 月

自動的に検出されたもの以外の言語でインストーラーをダウンロードする必要がある場合は、以下の直接リンクを使用できます。  
X64 ドライバーの場合: [簡体中国語](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x804) | [繁体中国語](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x40a)  
X86 ドライバーの場合: [簡体中国語](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x804) | [繁体中国語](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x40a)  

### <a name="features-added-in-1823"></a>18.2.3 で追加された機能

| 追加された機能 | 詳細 |
| :------------ | :------ |
| SQL Server リムーバブル メディアからのドライバーのアップグレードのサポート。 | この機能強化により、SQL Server リムーバブル メディアから直接ドライバーをアップグレードできます。 |
| &nbsp; | &nbsp; |

## <a name="1822"></a>18.2.2

![ダウンロード](../../ssms/media/download-icon.png) [x64 インストーラーのダウンロード](https://go.microsoft.com/fwlink/?linkid=2118512)  
![ダウンロード](../../ssms/media/download-icon.png) [x86 インストーラーのダウンロード](https://go.microsoft.com/fwlink/?linkid=2118415)  

リリース日:2019 年 5 月

自動的に検出されたもの以外の言語でインストーラーをダウンロードする必要がある場合は、以下の直接リンクを使用できます。  
X64 ドライバーの場合: [簡体中国語](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x804) | [繁体中国語](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x40a)  
X86 ドライバーの場合: [簡体中国語](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x804) | [繁体中国語](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x40a)  

### <a name="bugs-fixed-in-1822"></a>18.2.2 で修正されたバグ

| 修正されたバグ | 詳細 |
| :-------- | :------ |
| マルチスレッド アパートメント (MTA) で対話しない Azure Active Directory 認証を修正しました。 | マルチスレッド (MTA) として以前に初期化されたアパートメントで OLE DB Driver 18.2.1 が COM 同時実行モデルを誤って変更しようとします。 その結果、[IDBInitialize::Initialize](https://go.microsoft.com/fwlink/?linkid=2092522) インターフェイスを呼び出す前に 2 回以上 [CoInitialize](https://go.microsoft.com/fwlink/?linkid=2092520) または [CoInitializeEx](https://go.microsoft.com/fwlink/?linkid=2092521) に呼び出しを行うアプリケーションで、いずれかの Azure Active Directory 認証モードを使用するとドライバーが接続に失敗します。 |
| &nbsp; | &nbsp; |

## <a name="1821"></a>18.2.1

![ダウンロード](../../ssms/media/download-icon.png) [x64 インストーラーのダウンロード](https://go.microsoft.com/fwlink/?linkid=2118511)  
![ダウンロード](../../ssms/media/download-icon.png) [x86 インストーラーのダウンロード](https://go.microsoft.com/fwlink/?linkid=2118278)  

リリース日:2019 年 2 月

自動的に検出されたもの以外の言語でインストーラーをダウンロードする必要がある場合は、以下の直接リンクを使用できます。  
X64 ドライバーの場合: [簡体中国語](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x804) | [繁体中国語](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x40a)  
X86 ドライバーの場合: [簡体中国語](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x804) | [繁体中国語](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x40a)  

### <a name="features-added-in-1821"></a>18.2.1 で追加された機能

| 追加された機能 | 詳細 |
| :------------ | :------ |
| UTF-8 サーバー エンコードのサポート。 | [OLE DB Driver for SQL Server の UTF-8 サポート](features/utf-8-support-in-oledb-driver-for-sql-server.md)。 |
| Azure Active Directory 認証のサポート。 | [Azure Active Directory の使用](features/using-azure-active-directory.md)。 |
| &nbsp; | &nbsp; |

## <a name="1810"></a>18.1.0

![ダウンロード](../../ssms/media/download-icon.png) [x64 インストーラーのダウンロード](https://go.microsoft.com/fwlink/?linkid=2118506)  
![ダウンロード](../../ssms/media/download-icon.png) [x86 インストーラーのダウンロード](https://go.microsoft.com/fwlink/?linkid=2118509)  

リリース日:2018 年 7 月

自動的に検出されたもの以外の言語でインストーラーをダウンロードする必要がある場合は、以下の直接リンクを使用できます。  
X64 ドライバーの場合: [簡体中国語](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x804) | [繁体中国語](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x40a)  
X86 ドライバーの場合: [簡体中国語](https://go.microsoft.com/fwlink/?linkid=2118509&2118509=0x804) | [繁体中国語](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x40a)  

### <a name="features-added-in-1810"></a>18.1.0 で追加された機能

| 追加された機能 | 詳細 |
| :------------ | :------ |
| `UseFMTONLY` 接続文字列キーワードと `SSPROP_INIT_USEFMTONLY` 初期化プロパティのサポート。 | `UseFMTONLY` は [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以上に接続する場合のメタデータの取得方法を制御します。<br/><br/>詳細については、次を参照してください。[OLE DB Driver for SQL Server での接続文字列キーワードの使用](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)。 |
| &nbsp; | &nbsp; |

### <a name="bugs-fixed-in-1810"></a>18.1.0 で修正されたバグ

| 修正されたバグ | 詳細 |
| :-------- | :------ |
| BCP フォーマット ファイルのバージョンの誤りを修正しました。 | OLE DB Driver 18.0 では BCP フォーマット ファイルのバージョンが 11.0 ではなく 18.0 と誤って設定されています。<br/>OLE DB Driver 18.0 で生成されたフォーマット ファイルは OLE DB Driver 18.1 で読み取ることができません。<br/>以前のバージョンのドライバーで生成されたフォーマット ファイルを新しいドライバーで使用する必要がある場合、ファイルを手動で編集してバージョンを 11.0 に変更することができます。 |
| &nbsp; | &nbsp; |

## <a name="1802"></a>18.0.2

![ダウンロード](../../ssms/media/download-icon.png) [x64 インストーラーのダウンロード](https://go.microsoft.com/fwlink/?linkid=2118504)  
![ダウンロード](../../ssms/media/download-icon.png) [x86 インストーラーのダウンロード](https://go.microsoft.com/fwlink/?linkid=2118277)  

リリース日:2018 年 3 月

自動的に検出されたもの以外の言語でインストーラーをダウンロードする必要がある場合は、以下の直接リンクを使用できます。  
X64 ドライバーの場合: [簡体中国語](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x804) | [繁体中国語](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x40a)  
X86 ドライバーの場合: [簡体中国語](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x804) | [繁体中国語](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x40a)  

### <a name="features-added-in-1802"></a>18.0.2 で追加された機能

| 追加された機能 | 詳細 |
| :------------ | :------ |
| `MultiSubnetFailover` 接続文字列キーワードと `SSPROP_INIT_MULTISUBNETFAILOVER` 初期化プロパティのサポート。 | 詳細については、次を参照してください。<br/>&bull; &nbsp; [OLE DB Driver for SQL Server の高可用性、ディザスター リカバリーに関するサポート](features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)<br/>&bull; &nbsp; [OLE DB Driver for SQL Server での接続文字列キーワードの使用](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)。 |
| &nbsp; | &nbsp; |

## <a name="see-also"></a>関連項目

[Microsoft OLE DB Driver for SQL Server](oledb-driver-for-sql-server.md)
