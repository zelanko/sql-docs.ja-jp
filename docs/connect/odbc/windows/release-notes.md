---
title: リリース ノート (ODBC Driver for SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b8459ed8-625e-4d8b-891c-e7e78c9977cc
caps.latest.revision: 7
author: MightyPen
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: 1aa3823813392c660c8e31fc517ec4b7ae2e1e29
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39661874"
---
# <a name="release-notes"></a>リリース ノート
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

  Microsoft ODBC Driver for SQL Server on Windows のリリース ノート  

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-172-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Windows での [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.2 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] の新機能

**追加された機能**:

Azure SQL Database と SQL Server の詳細については、データの分類を参照してください[データ分類](../data-classification.md)

[バグの修正](../bug-fixes.md)

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Windows での [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] の新機能

**追加された機能**:

サポート`SQL_COPT_SS_CEKCACHETTL`と`SQL_COPT_SS_TRUSTEDCMKPATHS`接続属性 (詳細については、次を参照してください[ODBC Driver for SQL Server で Always Encrypted を使用して](../using-always-encrypted-with-the-odbc-driver.md))。
- `SQL_COPT_SS_CEKCACHETTL` 列暗号化キーのローカル キャッシュが存在する時間を制御するためにフラッシュできます。
- `SQL_COPT_SS_TRUSTEDCMKPATHS` により、アプリケーションは指定されたリストの列マスター_キーのだけを使用する AE 操作を制限するには


Azure Active Directory 対話型認証のサポート

[バグの修正](../bug-fixes.md)


## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Windows での [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] の新機能

**追加された機能**:

Always Encrypted のサポートの BCP API

新しい接続文字列属性 UseFMTOnly により一時テーブルを必要とする特殊なケースで、従来のメタデータを使用します。

Azure SQL マネージ インスタンス (延長プライベート プレビュー) をサポートします。 
> [!NOTE]
> マネージ インスタンスを使用する場合は、多くの違いにがあります。
> -   FILESTREAM がサポートされていません 
> -   ローカル ファイル システム アクセスがない、サポートされているが tracefiles などに必要な 
> -   ローカルから UDT を作成するパスはサポートされていません 
> -   Windows 統合認証はサポートされていません 
> -   DTC はサポートされていません 
> -   'sa' アカウントが存在しない (既定のアカウントと呼びます 'cloudSA')
> -   TDS トークン エラー (0xAA) が正しくないサーバー名を返します
> -   データベース名に特殊文字はサポートされていません 
> -   [Dbname1] ALTER DATABASE MODIFY NAME = [dbname2] はサポートされていません
> -   エラー メッセージが英語では、言語に関係なく常に表示される設定 (Azure と同じ) 
  

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-131-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Windows での [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] の新機能  
 ODBC Driver 13.1 for[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]のサポートが追加[Always Encrypted](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)と[Azure Active Directory](../../../connect/odbc/using-azure-active-directory.md) Microsoft SQL Server 2016 と組み合わせて使用するとします。  対応する接続のプーリング キーワードと属性については、「 [ODBC Driver for SQL Server でのドライバー対応接続プール](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)します。

 ## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-13-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Windows での [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] の新機能  
 ODBC Driver 13 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] SQL Server 用 ODBC Driver 11 から以前の機能が含まれていて、Microsoft SQL Server 2016 のサポートを追加します。

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-11-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Windows での [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] の新機能  
 ODBC Driver 11 for SQL Server には、SQL Server 2012 Native Client の ODBC が備えていたすべての機能に加えて、新しい[機能](./features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)が含まれます。  
