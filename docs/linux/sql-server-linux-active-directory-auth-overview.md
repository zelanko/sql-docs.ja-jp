---
title: Linux 上の SQL Server の active Directory 認証 |Microsoft ドキュメント
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
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
ms.locfileid: "34320933"
---
# <a name="active-directory-authentication-for-sql-server-on-linux"></a>Linux 上の SQL Server の active Directory 認証

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事は、Active Directory (AD) の認証の概要を説明[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Linux にします。 AD の認証とも呼ばれますで統合認証[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]です。 

## <a name="ad-authentication-overview"></a>AD 認証の概要

AD の認証により、クライアントへの認証に Windows または Linux ではドメインに参加している[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ドメイン資格情報と、Kerberos プロトコルを使用します。

AD 認証は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証に対して次の利点があります。

- ユーザーは、パスワードの入力を求められず、シングル サインオンを使用して認証します。   
- AD グループのログインを作成すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] AD グループのメンバーシップを使用してアクセスおよびアクセス許可を管理することができます。  
- 各ユーザーが組織全体で単一の ID を持っているので、どの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ログインがどのユーザーに対応するかを追跡する必要がありません。   
- AD では、組織全体で一元的なパスワード ポリシーを適用することができます。   

## <a name="configuration-steps"></a>構成手順

Active Directory 認証を使用するために、ネットワーク上に AD ドメイン コント ローラー (Windows) が必要です。

AD の認証を構成する方法の詳細については、チュートリアルの中の [チュートリアル: SQL Server on Linux で使用する Active Directory 認証](sql-server-linux-active-directory-authentication.md) で説明されています。 このチュートリアルでの各セクションへのリンクの概要を次に示します。

1. [SQL Server ホストを Active Directory ドメインに結合する](sql-server-linux-active-directory-authentication.md#join)
1. [SQL Server の AD ユーザーを作成し、ServicePrincipalName を設定する](sql-server-linux-active-directory-authentication.md#createuser)
1. [SQL Server サービス keytab を構成する](sql-server-linux-active-directory-authentication.md#configurekeytab)
1. [TRANSACT-SQL での SQL Server の AD に基づくログインの作成](sql-server-linux-active-directory-authentication.md#createsqllogins)
1. [AD 認証を使用して SQL Server に接続する](sql-server-linux-active-directory-authentication.md#connect)

## <a name="known-issues"></a>既知の問題

- この時点では、データベース ミラーリング エンドポイントでサポートされる唯一の認証方法は、証明書です。 WINDOWS 認証方法は、将来のリリースで有効にするされます。
- Centrify、Powerbroker および Vintela などのサード パーティ製 AD ツールはサポートされていません。

## <a name="next-steps"></a>次の手順

Linux に SQL Server の Active Directory 認証を実装する方法の詳細については、[チュートリアル: SQL Server on Linux で使用する Active Directory 認証](sql-server-linux-active-directory-authentication.md) を参照してください。