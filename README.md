## Creating New Blocks

This guide explains how to add new blocks to the Mukto Blocks plugin.

### Step 1: Create the Block

Navigate to the source directory:
```bash
cd src
```

Generate a new block using one of these commands:

**For Static Blocks:**
```bash
npx @wordpress/create-block@latest <block-name> --no-plugin
```
**For Dynamic Blocks:**
```bash
npx @wordpress/create-block@latest <block-name> --no-plugin --variant dynamic
```
### Step 2: Register the Block
Open `mukto-blocks.php` in the main plugin directory and add your new block to the `$blocks` array:

```php
function create_block_mukto_blocks_block_init() {
    $blocks = array(
        // Existing blocks...
        '<block-name>'  // Add your new block name here
    );
    foreach ($blocks as $block) {
        register_block_type( __DIR__ . "/build/$block" );
    }
}
add_action( 'init', 'create_block_mukto_blocks_block_init' );
```

