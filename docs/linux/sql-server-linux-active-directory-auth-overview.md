---
title: Linux 上の SQL Server の active Directory の認証 |Microsoft Docs
description: この記事では、Linux 上の SQL Server の Active Directory 認証の概要を示します。
author: rothja
ms.date: 02/23/2018
ms.author: jroth
manager: craigg
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: 7f34cda192cbd909ac6c2392ab49acb58038b416
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38020494"
---
# <a name="active-directory-authentication-for-sql-server-on-linux"></a>Linux 上の SQL Server の active Directory 認証

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事は、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on Linux における Active Directory (AD) 認証の概要を説明します。 AD 認証は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] で統合認証とも呼ばれています。 

## <a name="ad-authentication-overview"></a>AD 認証の概要

AD 認証を使用への認証に Windows または Linux 上のクライアントのドメインに参加している[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ドメイン資格情報と、Kerberos プロトコルを使用します。

AD 認証は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証に対して次の利点があります。

- ユーザーは、パスワードを入力することがなくシングル サインオンを使用して認証できます。   
- AD グループのログインを作成すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] AD グループのメンバーシップを使用してアクセスおよびアクセス許可を管理することができます。  
- 各ユーザーが組織全体で単一の ID を持っているので、どの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ログインがどのユーザーに対応するかを追跡する必要がありません。   
- AD では、組織全体で一元的なパスワード ポリシーを適用することができます。   

## <a name="configuration-steps"></a>構成手順

Active Directory 認証を使用するには、ネットワーク上に AD ドメイン コント ローラー (Windows) が必要です。

AD の認証を構成する方法の詳細については、チュートリアルの中の [チュートリアル: SQL Server on Linux で使用する Active Directory 認証](sql-server-linux-active-directory-authentication.md) で説明されています。 このチュートリアルでの各セクションへのリンクの概要を次に示します。

1. [SQL Server ホストを Active Directory ドメインに結合する](sql-server-linux-active-directory-authentication.md#join)
2. [SQL Server の AD ユーザーを作成し、ServicePrincipalName を設定する](sql-server-linux-active-directory-authentication.md#createuser)
3. [SQL Server サービス keytab を構成する](sql-server-linux-active-directory-authentication.md#configurekeytab)
4. [TRANSACT-SQL での SQL Server の AD に基づくログインの作成](sql-server-linux-active-directory-authentication.md#createsqllogins)
5. [AD 認証を使用して SQL Server に接続する](sql-server-linux-active-directory-authentication.md#connect)

## <a name="known-issues"></a>既知の問題

- この時点では、データベース ミラーリング エンドポイントでサポートされる唯一の認証方法は、証明書です。 将来のリリースでは、WINDOWS 認証方法を有効になります。
- Centrify、Powerbroker および Vintela などのサード パーティ製 AD ツールはサポートされていません。

## <a name="next-steps"></a>次の手順

Linux に SQL Server の Active Directory 認証を実装する方法の詳細については、[チュートリアル: SQL Server on Linux で使用する Active Directory 認証](sql-server-linux-active-directory-authentication.md) を参照してください。
