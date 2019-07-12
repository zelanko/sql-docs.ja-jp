---
title: Linux 上の SQL Server の active Directory 認証
titleSuffix: SQL Server
description: この記事では、Linux 上の SQL Server の Active Directory 認証の概要を示します。
ms.date: 04/01/2019
author: Dylan-MSFT
ms.author: dygray
ms.reviewer: vanto
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: 14cb6a377e6aeb0fbd24f9808a794d68633f4ce6
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67834421"
---
# <a name="active-directory-authentication-for-sql-server-on-linux"></a>Linux 上の SQL Server の active Directory 認証

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事は、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on Linux における Active Directory (AD) 認証の概要を説明します。 AD 認証は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] で統合認証とも呼ばれています。 

## <a name="ad-authentication-overview"></a>AD 認証の概要

AD 認証を使用への認証に Windows または Linux 上のクライアントのドメインに参加している[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ドメイン資格情報と、Kerberos プロトコルを使用します。

AD 認証は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証に対して次の利点があります。

- ユーザーは、パスワードを入力することがなくシングル サインオンを使用して認証できます。   
- AD グループのログインを作成すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] AD グループのメンバーシップを使用してアクセスおよびアクセス許可を管理することができます。  
- 追跡をする必要はありませんので、各ユーザーが組織全体で単一の id が[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ログインは、どのユーザーに対応します。   
- AD では、組織全体で一元的なパスワード ポリシーを適用することができます。   

## <a name="configuration-steps"></a>構成手順

Active Directory 認証を使用するには、ネットワーク上に AD ドメイン コント ローラー (Windows) が必要です。

AD 認証を構成する方法の詳細については、チュートリアルでは提供されている[チュートリアル。SQL Server on Linux での Active Directory 認証の使用](sql-server-linux-active-directory-authentication.md)します。 このチュートリアルでの各セクションへのリンクの概要を次に示します。

1. [SQL Server ホストを Active Directory ドメインに結合する](sql-server-linux-active-directory-join-domain.md)
1. [SQL Server の AD ユーザーを作成し、ServicePrincipalName を設定する](sql-server-linux-active-directory-authentication.md#createuser)
1. [SQL Server サービス keytab を構成する](sql-server-linux-active-directory-authentication.md#configurekeytab)
1. [Keytab ファイルをセキュリティで保護された](sql-server-linux-active-directory-authentication.md#securekeytab)します。
1. [Kerberos 認証に keytab ファイルを使用する SQL Server 構成](sql-server-linux-active-directory-authentication.md#keytabkerberos)します。
1. [TRANSACT-SQL での SQL Server の AD に基づくログインの作成](sql-server-linux-active-directory-authentication.md#createsqllogins)
1. [AD 認証を使用して SQL Server に接続する](sql-server-linux-active-directory-authentication.md#connect)

## <a name="known-issues"></a>既知の問題

- この時点では、データベース ミラーリング エンドポイントでサポートされる唯一の認証方法は、証明書です。 将来のリリースでは、WINDOWS 認証方法を有効になります。

## <a name="next-steps"></a>次の手順

Linux 上の SQL Server の Active Directory 認証を実装する方法の詳細については、次を参照してください。[チュートリアル。SQL Server on Linux での Active Directory 認証の使用](sql-server-linux-active-directory-authentication.md)します。
