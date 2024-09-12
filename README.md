# Bedrock Texturepack Encoder

This GitHub Action is designed to streamline the encryption process of Minecraft Bedrock Edition texture packs. Using the [mcrputil](https://github.com/valaphee/mcrputil) tool, this action encrypts a given texture pack with a specified key and generates an encrypted artifact.

# What's new

Please refer to the [release page](https://github.com/zelytra/bedrock-texturepack-encryption/releases/latest) for the latest release notes.

# Usage

<!-- start usage -->
```yaml
- uses: zelytra/bedrock-texturepack-encryption@v1
  with:
    # The private key used to encode your texture pack
    # Default: ${{ github.repository }}
    private_key: ''
    
    # The path of your texture pack root folder
    # Default: ${{ github.workspace }}
    texture_pack_path: ''
    
    # The name of your texture pack
    # Default: "no-name"
    texture_pack_name: ''

    # Path where the encoded texture pack will be saved
    # Default: ${{ github.workspace }}/encoded_pack
    output_encoded_path: ''
```
<!-- end usage -->

# Scenarios

- [Basic texturepack encryption](#Basic-texturepack-encryption)
- [Basic texturepack encryption and zipping the result](#Basic-texturepack-encryption-and-zipping-the-result)

## Basic texturepack encryption

```yaml
- name: Run custom Bedrock Texturepack Encryption Action
  uses: zelytra/bedrock-texturepack-encryption@v1
  with:
    private_key: ${{ secrets.ENCRYPTION_KEY }} # Replace with a test key or use secrets 32 characters (a-Z,0.9)
    texture_pack_path: 'my-texturepack' # Path to the example pack in the repo
    texture_pack_name: 'MyTexturePAck'
    output_encoded_path: './encoded-pack'
```

## Basic texturepack encryption and zipping the result

```yaml
- name: Run custom Bedrock Texturepack Encryption Action
  uses: zelytra/bedrock-texturepack-encryption@v1.0.0-beta
  with:
    private_key: ${{ secrets.ENCRYPTION_KEY }} # Replace with a test key or use secrets 32 characters (a-Z,0.9)
    texture_pack_path: 'my-texturepack' # Path to the example pack in the repo
    texture_pack_name: 'MyTexturePAck'
    output_encoded_path: './encoded-pack'
- name: Zip encrypted texture pack
  run: cd ./encoded-pack/MyTexturePAck && zip -r ../../MyTexturePAck.zip ./*
```

# License

The scripts and documentation in this project are released under the [MIT License](LICENSE)
