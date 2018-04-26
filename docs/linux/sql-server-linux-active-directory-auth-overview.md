---
title: Linux 上の SQL Server の active Directory 認証 |Microsoft ドキュメント
description: この記事では、Linux 上の SQL Server の Active Directory 認証の概要を示します。
author: rothja
ms.date: 02/23/2018
ms.author: jroth
manager: craigg
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
helpviewer_keywords:
- Linux, AAD authentication
ms.workload: On Demand
ms.openlocfilehash: bd4ba9f12b7567f618db2aef1adb87a8f1f080f5
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="active-directory-authentication-for-sql-server-on-linux"></a>Linux 上の SQL Server の active Directory 認証

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事は、Active Directory (AD) の認証の概要を説明[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Linux にします。 AD の認証とも呼ばれますで統合認証[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]です。 

## <a name="ad-authentication-overview"></a>AD 認証の概要

AD の認証により、クライアントへの認証に Windows または Linux ではドメインに参加している[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ドメイン資格情報と、Kerberos プロトコルを使用します。

AD 認証経由では次の利点があります[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]認証。

- ユーザーは、パスワードの入力を求められず、シングル サインオンを使用して認証します。   
- アクセスおよびアクセス許可を管理する AD グループのログインを作成すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] AD グループのメンバーシップを使用します。  
- を追跡する必要はありません、各ユーザーが組織全体で単一の id を持って[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ログインは、どのユーザーに対応します。   
- AD では、組織全体で一元的なパスワード ポリシーを適用することができます。   

## <a name="configuration-steps"></a>構成手順

Active Directory 認証を使用するために、ネットワーク上に AD ドメイン コント ローラー (Windows) が必要です。

AD の認証を構成する方法の詳細については、チュートリアルの説明[チュートリアル: SQL Server on Linux で使用する Active Directory 認証](sql-server-linux-active-directory-authentication.md)です。 このチュートリアルでの各セクションへのリンクの概要を次に示します。

1. [Active Directory ドメインに SQL Server ホストに参加](sql-server-linux-active-directory-authentication.md#join)です。
1. [SQL Server の AD ユーザーを作成し、ServicePrincipalName を設定](sql-server-linux-active-directory-authentication.md#createuser)です。
1. [SQL Server サービス keytab を構成する](sql-server-linux-active-directory-authentication.md#configurekeytab)です。
1. [TRANSACT-SQL での SQL Server の AD に基づくログインの作成](sql-server-linux-active-directory-authentication.md#createsqllogins)です。
1. [AD 認証を使用して SQL Server に接続](sql-server-linux-active-directory-authentication.md#connect)です。

## <a name="known-issues"></a>既知の問題

- この時点では、データベース ミラーリング エンドポイントでサポートされる唯一の認証方法は、証明書です。 WINDOWS 認証方法は、将来のリリースで有効にするされます。
- Centrify、Powerbroker などのサード パーティ製 AD ツールおよびいる Vintela はサポートされていません。

## <a name="next-steps"></a>次の手順

Linux に SQL Server の Active Directory 認証を実装する方法の詳細については、次を参照してください。[チュートリアル: SQL Server on Linux で使用する Active Directory 認証](sql-server-linux-active-directory-authentication.md)です。