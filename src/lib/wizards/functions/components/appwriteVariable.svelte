<script lang="ts">
    import { Box } from '$lib/components';
    import { FormList, Helper, InputChoice, InputPassword } from '$lib/elements/forms';
    import type { Variable } from '$lib/stores/marketplace';
    import { templateConfig } from '../store';

    export let appwriteVariable: Variable;
</script>

<Box radius="small" padding={16}>
    <FormList>
        <div>
            <InputPassword
                id={appwriteVariable.name}
                label={appwriteVariable.name}
                placeholder={appwriteVariable.placeholder ?? 'Enter value'}
                showPasswordButton
                required={appwriteVariable.required && !$templateConfig.generateKey}
                bind:value={$templateConfig.appwriteApiKey}
                disabled={!!$templateConfig.generateKey} />
            <Helper type="neutral">
                This API key will allow you to interact with the Appwrite server APIs. <a
                    href="https://localhost/docs/advanced/platform/api-keys"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="link">Learn more</a
                >.
            </Helper>
        </div>
        <InputChoice
            bind:value={$templateConfig.generateKey}
            id="generate"
            label="Generate API key on completion"
            disabled={!!$templateConfig.appwriteApiKey}>
            The <code class="inline-code">APPWRITE_API_KEY</code> will be automatically generated for
            your project and applied to this function once it's created.
        </InputChoice>
    </FormList>
</Box>
