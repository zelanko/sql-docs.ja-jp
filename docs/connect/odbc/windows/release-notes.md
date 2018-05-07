---
title: リリース ノート (SQL Server 用 ODBC Driver) |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/04/2018
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
ms.author: genemi
manager: craigg
ms.openlocfilehash: 21380decd228d82695c4ca9972852585a4fc3dbc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="release-notes"></a>リリース ノート
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

  Microsoft ODBC Driver for SQL Server on Windows のリリース ノート  

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>新機能、[!INCLUDE[msCoName](../../../includes/msconame_md.md)]用 ODBC Driver 17.1 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] windows

**追加された機能**:

サポート`SQL_COPT_SS_CEKCACHETTL`と`SQL_COPT_SS_TRUSTEDCMKPATHS`接続属性 (詳細については、次を参照してください[for SQL Server ODBC ドライバーで Always Encrypted を使用して](../using-always-encrypted-with-the-odbc-driver.md))。
- `SQL_COPT_SS_CEKCACHETTL` により、列暗号化キーのローカル キャッシュが存在する、時間を制御するだけでなく、フラッシュ
- `SQL_COPT_SS_TRUSTEDCMKPATHS` により、アプリケーション リストだけを使用して、指定された列マスター_キーの AE 操作を制限するには


Azure Active Directory の対話型の認証のサポート

[バグの修正](../bug-fixes.md)


## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>新機能、[!INCLUDE[msCoName](../../../includes/msconame_md.md)]用 ODBC Driver 17 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] windows

**追加された機能**:

BCP API が常に暗号化されたサポート

新しい接続文字列属性 UseFMTOnly には、一時テーブルを必要とする特殊なケースで以前のメタデータを使用するドライバーが原因です。

Azure SQL のマネージ インスタンス (拡張プライベート プレビュー) をサポートします。 
> [!NOTE]
> さまざまな違いがあるマネージ インスタンスを使用する場合。
> -   FILESTREAM がサポートされていません 
> -   ローカル ファイル システム アクセスはサポートされている、せずに tracefiles などのために必要な 
> -   ローカル コンピューターから UDT を作成するパスはサポートされていません 
> -   Windows 統合認証はサポートされていません 
> -   DTC がサポートされていません 
> -   'sa' アカウントが存在しない (既定のアカウントと呼びます 'cloudSA')
> -   TDS トークン エラー (0xAA) が正しくないサーバー名を返します
> -   データベース名に特殊文字はサポートされていません 
> -   ALTER DATABASE [dbname1] MODIFY NAME = [dbname2] is not supported
> -   エラー メッセージが英語では、言語に関係なく常に表示される設定 (Azure と同じ) 
  

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-131-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>新機能、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] windows  
 用 ODBC Driver 13.1[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]のサポートが追加[Always Encrypted](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)と[Azure Active Directory](../../../connect/odbc/using-azure-active-directory.md) Microsoft SQL Server 2016 と組み合わせて使用するとします。  対応する接続のプーリング キーワードと属性は「 [ODBC Driver for SQL Server でのドライバー対応接続プール](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)です。

 ## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-13-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>新機能、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] windows  
 ODBC Driver 13 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] SQL Server 用 ODBC Driver 11 から以前の機能が含まれていて、Microsoft SQL Server 2016 のサポートを追加します。

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-11-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>新機能、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] windows  
 ODBC Driver 11 for SQL Server を含む新しい[機能](./features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)SQL Server 2012 Native Client の ODBC に同梱されているすべての機能とします。  
