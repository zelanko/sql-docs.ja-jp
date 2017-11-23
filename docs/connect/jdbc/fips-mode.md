---
title: "FIPS モード |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/28/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: "1"
author: v-nisidh
ms.author: v-nisidh
manager: andrela
ms.workload: Inactive
ms.openlocfilehash: 29ddc84524d87b4277b1dc4efc4431c4f9c5f5d5
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="fips-mode"></a>FIPS モード
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Microsoft JDBC Driver for SQL Server をサポートしている*FIPS 140 準拠モード*です。 For Oracle を参照してください、Sun JVM/、 [FIPS 140 準拠モードによって](https://docs.oracle.com/javase/7/docs/technotes/guides/security/jsse/FIPS.html)FIPS を構成する Oracle によって提供されるセクションには、JVM が有効になっています。 

**前提条件**:
* FIPS JVM を構成します。
* 適切な SSL 証明書。
* 適切なポリシー ファイルです。 
* 適切な構成パラメーターです。 


## <a name="fips-configured-jvm"></a>FIPS には、JVM が構成されています。

承認済みのモジュールは、FIPS 構成を参照してください、[検証 FIPS 140-1、FIPS 140-2 の暗号化モジュール](http://csrc.nist.gov/groups/STM/cmvp/documents/140-1/1401val2016.htm)です。 

ベンダーは、FIPS に JVM を構成する追加の手順があります。

### <a name="ensure-your-jvm-is-in-fips-mode"></a>JVM が FIPS モードでを確認します。
JVM が FIPS が有効になっていることを確認するには、するためには、次のスニペットを実行します。 

````
public boolean isFIPS() throws Exception {
    Provider jsse = Security.getProvider("SunJSSE");
    return jsse != null && jsse.getInfo().contains("FIPS");
}
````

## <a name="appropriate-ssl-certificate"></a>適切な SSL 証明書:
FIPS モードで SQL Server を接続するためには、有効な SSL 証明書が必要です。 インストールまたは FIPS が有効になって、クライアント マシン (JVM) の Java キー ストアにインポートします。 いないインポート/、適切な証明書をインストールして、セキュリティで保護された接続を確立できないと、SQL Server に接続できませんでしたできません。

### <a name="importing-ssl-certificate-in-java-keystore"></a>Java キーストアで SSL 証明書をインポートするには。
FIPS のほとんどの場合必要があります (して .cert) 証明書をインポートするか PKCS またはプロバイダー固有の書式。 次のスニペットを使用して、SSL 証明書をインポートし、適切なキーストア形式での作業ディレクトリに格納します。 _TRUST_STORE_PASSWORD_ Java キーストアのパスワードがします。 

````
    public void saveGenericKeyStore(String provider, String trustStoreType, String certName, String certPath) throws KeyStoreException, CertificateException, NoSuchAlgorithmException, NoSuchProviderException, IOException {
        KeyStore ks = KeyStore.getInstance(trustStoreType, provider);
        FileOutputStream os = new FileOutputStream("./MyTrustStore_" + trustStoreType);
        ks.load(null, null);
        ks.setCertificateEntry(certName, getCertificate(certPath));
        ks.store(os, TRUST_STORE_PASSWORD.toCharArray());
        os.flush();
        os.close();
    }

    private Certificate getCertificate(String pathName) throws FileNotFoundException, CertificateException {
        FileInputStream fis = new FileInputStream(pathName);
        CertificateFactory cf = CertificateFactory.getInstance("X.509");
        return cf.generateCertificate(fis);
    }

````


次の例では、Azure SSL 証明書をインポート PKCS12 形式で BouncyCastle プロバイダーとします。 という名前の作業ディレクトリに証明書をインポート_MyTrustStore_PKCS12_次のスニペットを使用しています。

` saveGenericKeyStore(BCFIPS, PKCS12, "SQLAzure SSL Certificate Name", "SQLAzure.cer"); `

## <a name="appropriate-policy-files"></a>適切なポリシー ファイル: 
FIPS プロバイダーによっては、無制限のポリシー jar ファイルが必要です。 このような場合、Sun/Oracle、ダウンロード、Java Cryptography Extension (JCE) 無制限 Strength Jurisdiction Policy Files の[JRE 8](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html)または[JRE 7](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html)です。 

## <a name="appropriate-configuration-parameters"></a>適切な構成パラメーター: 
FIPS 準拠モードでは、JDBC ドライバーを実行するためには、次の表に示すように、接続のプロパティを構成します。 

**プロパティ**: 

|プロパティ|型|既定値|Description|注|
|---|---|---|---|---|
|encrypt|ブール値を [「真/偽」]|"false"|JVM の暗号化プロパティ FIPS が有効にする必要があります**は true。**||
|TrustServerCertificate|ブール値を [「真/偽」]|"false"|FIPS が証明書チェーンを検証する必要がありますのように使用する**"false"**このプロパティの値。 ||
|trustStore|文字列|null|証明書をインポートした、Java Keystore ファイル パス。 システムに何も渡す必要はありません証明書をインストールする場合。 ドライバーは、cacerts または jssecacerts ファイルを使用します。||
|trustStorePassword|文字列|null|trustStore データの整合性を確認するために使用するパスワードです。||
|fips|ブール値を [「真/偽」]|"false"|このプロパティは、fips が JVM を有効になっている**は true。**|6.1.4 の追加||
|fipsProvider|文字列|null|JVM で構成されている FIPS プロバイダーです。 たとえば、BCFIPS または SunPKCS11 NSS |6.1.2 の追加|
|trustStoreType|文字列|JKS|PKCS12 または型のいずれかで FIPS プロバイダーによって定義 FIPS モード セット信頼ストアの種類 |6.1.2 の追加||



  
