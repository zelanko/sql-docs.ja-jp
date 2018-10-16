---
title: JDBC で FIPS モード |Microsoft Docs
ms.custom: ''
ms.date: 07/12/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: craigg
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daveng
manager: kenvh
ms.openlocfilehash: 1708bf5d1fbd47f7fb2dcefbbb5150d4b5646343
ms.sourcegitcommit: fff9db8affb094a8cce9d563855955ddc1af42d2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2018
ms.locfileid: "49324572"
---
# <a name="fips-mode"></a>FIPS モード
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Microsoft JDBC Driver for SQL Server サポート*FIPS 140 準拠モード*します。 For Oracle を参照してください、Sun JVM/、 [FIPS 140 準拠モード SunJSSE](https://docs.oracle.com/javase/7/docs/technotes/guides/security/jsse/FIPS.html) FIPS 構成に Oracle によって提供されるセクションには、JVM が有効になっています。 

#### <a name="prerequisites"></a>Prerequisites

- FIPS JVM を構成します。
- 適切な SSL 証明書。
- 適切なポリシー ファイルです。 
- 適切な構成パラメーター。 


## <a name="fips-configured-jvm"></a>FIPS JVM を構成します。

FIPS 構成には、承認済みのモジュールを参照してくださいを参照してください、[検証 FIPS 140-1 と FIPS 140-2 暗号化モジュール](http://csrc.nist.gov/groups/STM/cmvp/documents/140-1/1401val2016.htm)します。 

ベンダーは、FIPS JVM を構成する追加の手順があります。

### <a name="ensure-your-jvm-is-in-fips-mode"></a>JVM が FIPS モードを確認します。
JVM が FIPS を有効になっていることを確認するには、次のスニペットを実行します。 

```java
public boolean isFIPS() throws Exception {
    Provider jsse = Security.getProvider("SunJSSE");
    return jsse != null && jsse.getInfo().contains("FIPS");
}
```

## <a name="appropriate-ssl-certificate"></a>適切な SSL 証明書
FIPS モードで SQL Server を接続するためには、有効な SSL 証明書が必要です。 インストールまたは FIPS が有効になっているクライアント マシン (JVM) での Java キー ストアにインポートします。

### <a name="importing-ssl-certificate-in-java-keystore"></a>Java キーストアで SSL 証明書をインポートします。
FIPS のほとんどの場合必要があります (.cert) 証明書をインポートするか PKCS またはプロバイダー固有の書式。 SSL 証明書をインポートし、適切なキーストア形式での作業ディレクトリに保存するには、次のスニペットを使用します。 _信頼\_ストア\_パスワード_は Java キーストアのパスワードです。 


```java
public void saveGenericKeyStore(
        String provider,
        String trustStoreType,
        String certName,
        String certPath
        ) throws KeyStoreException, CertificateException,
            NoSuchAlgorithmException, NoSuchProviderException,
            IOException
{
    KeyStore ks = KeyStore.getInstance(trustStoreType, provider);
    FileOutputStream os = new FileOutputStream("./MyTrustStore_" + trustStoreType);
    ks.load(null, null);
    ks.setCertificateEntry(certName, getCertificate(certPath));
    ks.store(os, TRUST_STORE_PASSWORD.toCharArray());
    os.flush();
    os.close();
}

private Certificate getCertificate(String pathName)
        throws FileNotFoundException, CertificateException
{
    FileInputStream fis = new FileInputStream(pathName);
    CertificateFactory cf = CertificateFactory.getInstance("X.509");
    return cf.generateCertificate(fis);
}
```


次の例は BouncyCastle プロバイダーと PKCS12 形式で Azure SSL 証明書をインポートしています。 という名前の作業ディレクトリに証明書をインポート_MyTrustStore\_PKCS12_次のスニペットを使用します。

`saveGenericKeyStore(BCFIPS, PKCS12, "SQLAzure SSL Certificate Name", "SQLAzure.cer");`

## <a name="appropriate-policy-files"></a>適切なポリシー ファイル
FIPS プロバイダーによっては、無制限のポリシーの jar が必要です。 このような場合は、sun、/、Oracle Java Cryptography Extension (JCE) 無制限強度管轄ポリシーのファイルをダウンロード[JRE 8](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html)または[JRE 7](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html)します。 

## <a name="appropriate-configuration-parameters"></a>適切な構成パラメーター
FIPS 準拠モードでは、JDBC ドライバーを実行するには、次の表に示すように、接続のプロパティを構成します。 

#### <a name="properties"></a>[プロパティ] 

|プロパティ|型|既定|[説明]|注|
|---|---|---|---|---|
|encrypt|boolean ["true / false"]|"false"|JVM がプロパティを暗号化する FIPS が有効になっている必要があります**は true。**||
|TrustServerCertificate|boolean ["true / false"]|"false"|ユーザーは、FIPS のため、ユーザーが使用する必要があります、証明書チェーンを検証する必要があります **"false"** このプロパティの値。 ||
|trustStore|String|null|証明書をインポートする、Java Keystore ファイル パス。 証明書をインストールするには、システム上に何も渡す必要はありません。 場合、 ドライバーは、cacerts または jssecacerts ファイルを使用します。||
|trustStorePassword|String|null|trustStore データの整合性を確認するために使用するパスワードです。||
|fips|boolean ["true / false"]|"false"|このプロパティは、FIPS 対応 JVM**は true。**|6.1.4 で追加された (安定版 6.2.2 をリリース)||
|fipsProvider|String|null|JVM で構成されている FIPS プロバイダー。 たとえば、BCFIPS または SunPKCS11 NSS |6.1.2 で追加 (安定した 6.2.2 をリリース)、詳細を参照してください - 6.4.0 で非推奨と[ここ](https://github.com/Microsoft/mssql-jdbc/pull/460)します。|
|trustStoreType|String|JKS|FIPS モード セット信頼ストアの種類の PKCS12 または型プロバイダーによって定義された FIPS |6.1.2 で追加された (安定版 6.2.2 をリリース)||
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

