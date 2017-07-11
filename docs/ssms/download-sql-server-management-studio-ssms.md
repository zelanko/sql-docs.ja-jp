---
title: "SQL Server Management Studio (SSMS) のダウンロード | Microsoft Docs"
ms.custom: 
ms.date: 06/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "ssms のインストール、ssms のダウンロード、最新の ssms"
- SQL Server Management Studio
- ssms.exe
- sql man studio
- sql management studio
- "sql management studio インストール"
- "ダウンロード sql management studio"
- ms sql management studio
- install sql management studio
- ssms download
- sql server ssms
- ssms express
ms.assetid: adafeeef-4255-4924-8042-02f503d599ca
caps.latest.revision: 145
author: stevestein
ms.author: sstein
manager: craigg
ms.translationtype: Human Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 60bdb820d74be98dd051d4729463d375d2a5202a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/03/2017

---
<a id="download-sql-server-management-studio-ssms" class="xliff"></a>

# SQL Server Management Studio (SSMS) のダウンロード
SQL Server Management Studio (SSMS) は、SQL Server から SQL Database まで、SQL インフラストラクチャを管理するための統合環境です。 SSMS は、SQL を配置した任意の場所から、SQL のインスタンスを構成、監視、および管理することができるツールを備えています。 SSMS では、アプリケーションで使われるデータ層コンポーネントを配置、監視、アップグレードしたり、クエリとスクリプトを作成したりすることもできます。 

このリリースでは、以前のバージョンの SQL Server との互換性が強化され、スタンドアロン Web インストーラーを利用できるようになり、新しいリリースが入手可能になると SSMS 内でトースト通知が表示されるようになります。  
  
![ダウンロード](../ssdt/media/download.png) SSMS は無料です。 **[SQL Server Management Studio 17.1 をダウンロードする](https://go.microsoft.com/fwlink/?linkid=849819)** SSMS 17.X は、SQL Server Management Studio の最新世代であり、SQL Server 2017 をサポートしています。 

![ダウンロード](../ssdt/media/download.png) **[SQL Server Management Studio 17.1 アップグレード パッケージのダウンロード (17.0 から 17.1 へのアップグレード)](https://go.microsoft.com/fwlink/?linkid=849821)**

> [!NOTE]
> SQL Server PowerShell モジュールは、PowerShell ギャラリーで入手できる独立したインストールになりました。  詳しくは、[ダウンロードに関する説明](download-sql-server-ps-module.md)をご覧ください。

<a id="sql-server-management-studio" class="xliff"></a>

## [SQL Server Management Studio]   
**バージョン情報**  
  
リリース番号: 17.1  
このリリースのビルド番号: 14.0.17119.0

<a id="new-in-this-release" class="xliff"></a>

## このリリースの新機能  

SSMS 17.1 は、17.X 世代の SQL Server Management Studio の最初の更新プログラムです。  17.X 世代は、SQL Server 2008 から SQL Server 2017 までのほぼすべての機能領域をサポートしています。  また、バージョン 17.X は、SQL Analysis Service PaaS をサポートする SSMS の世代でもあります。

バージョン 17.1 の内容:

* ユーザーから報告された複数の問題の修正 
* 新しい Integration Services スケールアウト管理ツール

詳細な変更一覧については、以下を参照してください。   
                [SQL Server Management Studio - Changelog (SSMS)](../ssms/sql-server-management-studio-changelog-ssms.md)  
   
ユーザー データの収集については、次をご覧ください   
                [SQL Server のプライバシーに関する声明](http://www.microsoft.com/privacystatement/en-us/SQLServer/Default.aspx) 
  
<a id="supported-sql-offerings" class="xliff"></a>

## サポートされる SQL 製品
  
* このバージョンの SSMS は、すべての[サポート対象バージョンである SQL Server 2008 から SQL Server 2017](https://support.microsoft.com/en-us/lifecycle?C2=1044) で動作し、Azure SQL Database および Azure SQL Data Warehouse で最新のクラウド機能と連携するための最大レベルのサポートを提供します。  
* SQL Server 2000 または SQL Server 2005 に対して明示的なブロックはありませんが、一部の機能が適切に機能しない可能性があります。  
* また、SSMS 17.X は、SSMS 16.X または SQL Server 2014 SSMS 以前とサイドバイサイドでインストールできます。 
  
<a id="supported-operating-systems" class="xliff"></a>

## サポートされるオペレーティング システム
  
SSMS の今回のリリースでは、最新の Service Pack を使用した次のプラットフォームがサポートされます。   
- Windows 10
- Windows 8.1
- Windows 8
- Windows 7 (SP1)
- Windows Server 2016
- Windows Server 2012 (64 ビット) 
- Windows Server 2012 R2 (64 ビット) 
- Windows Server 2008 R2 (64 ビット)  

>[!NOTE]
>SSMS 17.X は、Windows Server 2016 より前にリリースされた Visual Studio 2015 Isolated Shell に基づいています。 Microsoft はアプリケーションの互換性を重視しており、既にリリースされているアプリケーションが最新の Windows リリースでも引き続き動作するように努めています。 Windows Server 2016 での SSMS の実行に関する問題を最小限に抑えるには、SSMS に最新の更新プログラムをすべて適用してください。 Windows Server 2016 での SSMS で問題が発生する場合は、サポートに問い合わせてください。 サポートは問題が SSMS、Visual Studio、または Windows の互換性のいずれに関するものかを判別し、問題を適切なチームに渡します。

<a id="ssms-installation-tips-and-issues" class="xliff"></a>

## SSMS のインストールに関するヒントと問題
**インストール時の再起動を最小限に抑える**

- SSMS のセットアップでインストールの最後に再起動が必要になる可能性を低くするには、次の操作を実行します。
  - 最新バージョンの Visual C++ 2013 再頒布可能パッケージを実行します。 バージョン 12.00.40649.5 (またはそれ以降) が必要です。 必要なのは x64 バージョンのみです。
  - コンピューターの .NET Framework のバージョンが 4.6.1 (またはそれ以降) であることを確認します。
  - コンピューターで Visual Studio のインスタンスが他に開かれている場合はすべて閉じます。
  - OS の最新の更新プログラムがすべてコンピューターにインストールされていることを確認します。
  - 通常、示されている操作は 1 回だけ必要です。 SSMS の同じメジャー バージョンに対する追加アップグレードの間に、再起動が必要になる場合があります。 マイナー アップグレードでは、SSMS のすべての前提条件は既にコンピューターにインストールされています。

- 既知の問題と回避策の一覧については、「[SQL Server Management Studio - リリース ノート](../ssms/sql-server-management-studio-release-notes.md)」をご覧ください。

<a id="available-languages" class="xliff"></a>

## 使用できる言語  
> SSMS の英語以外のローカライズされたリリースでは、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 にインストールする場合、 [KB 2862966 セキュリティ更新プログラム パッケージ](https://support.microsoft.com/en-us/kb/2862966) が必要です。 
  
SSMS の今回のリリースは、次の言語でインストールできます。

SQL Server Management Studio 17.1:<br>
[中国語 (中華人民共和国)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x804) | [中国語 (台湾)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40a)

SQL Server Management Studio 17.1 アップグレード パッケージ (17.0 から 17.1 へのアップグレード):<br>
[中国語 (中華人民共和国)](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x804) | [中国語 (台湾)](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x40a)

<a id="previous-releases" class="xliff"></a>

## 以前のリリース  
[SQL Server Management Studio の以前のリリース](../ssms/previous-sql-server-management-studio-releases.md)  
  
<a id="feedback" class="xliff"></a>

## フィードバック  
  
![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [SQL Client Tools Forum](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Microsoft Connect で問題や提案を記録](https://connect.microsoft.com/SQLServer/Feedback)  
  
<a id="see-also" class="xliff"></a>

## 参照  
[チュートリアル: SQL Server Management Studio](http://msdn.microsoft.com/en-us/d2bade70-07cf-4d94-b5d2-88aecb538ed1)  
[SQL Server Management Studio のドキュメント](https://msdn.microsoft.com/library/hh213248(v=sql.130).aspx)  
[Microsoft SQL Server](https://msdn.microsoft.com/library/bb545450.aspx)  
[追加の更新プログラムとサービス パック](https://technet.microsoft.com/sqlserver/ff803383.aspx)  
[SQL Server Data Tools (SSDT) のダウンロード](../ssdt/download-sql-server-data-tools-ssdt.md)  



